# Running Benchmarking Pipeline (Nextflow/Snakemake) on an Example Dataset using AWS

This tutorial provides step-by-step instructions to run the benchmarking pipeline on an AWS EC2 instance using a bundled example dataset.

All required input files (POD5 and reference genome) are available in the `example/` directory.

---

## AWS Instance Configuration

The pipeline was tested on the following AWS setup:

- **Instance type:** `gr6.4xlarge`  
  *(16 vCPUs, 128 GB RAM, 1 GPU)*  
- **AMI:** Deep Learning OSS Nvidia Driver AMI (Ubuntu 24.04)  
- **Storage:** 150 GB GP3 root volume  

> Ensure sufficient disk space and GPU availability for optimal performance.

---

## Input Files

### Example dataset (Default)

The repository includes a minimal dataset:

- **POD5 files:** `example/pod5/`  
- **Reference genome:** `example/references/H.pylori_J99_ATCC700824.fa`

---

### Alternative: Download Data from AWS RODA

Instead of using the bundled example data, you can download datasets from the Registry of Open Data on AWS (RODA) and replace them with the example dataset in the corresponding directories.

The following steps require the AWS CLI to be installed:  
https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html

---

Downloading Escherichia coli str. K-12 substr. MG1655 sample and corresponding reference file.
#### 1. Download sample POD5 files

```bash
aws s3 sync --no-sign-request \
    s3://ont-basemod-benchmark-data/Raw/pod5/bacteria/Ecoli_WT_5kHz/ \
    example/pod5/Ecoli_WT_5kHz/
```
#### 2. Download sample reference file

```bash
aws s3 cp --no-sign-request \
    s3://ont-basemod-benchmark-data/Analysis/Reference/ecoli.fa.gz \
    example/references/
```
> **Note:** After downloading, ensure the reference file is uncompressed before running the pipeline.


## Setting up the environment
1. `sudo apt update && sudo apt install samtools openjdk-17-jdk git wget -y` (if on a debian machine)
2. Install [docker](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-22-04)
  - setup docker to run without sudo
      ```bash
      sudo groupadd docker
      sudo usermod -aG docker $USER
      newgrp docker
      ```
  - test if everything is working: 
      ```
      docker run hello-world
      ```
3. Install apptainer:
    https://apptainer.org/

    on a debian machine:
   ```
    sudo add-apt-repository -y ppa:apptainer/ppa
    sudo apt update
    sudo apt install -y apptainer-suid
   ```

4. Install conda:
    ```
    wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O miniconda.sh
    bash miniconda.sh -b -u
    ~/miniconda3/bin/conda init bash 
    source ~/.bashrc 
    conda tos accept
    ```
5. Install [nextflow](https://www.nextflow.io/) 
    ```
    curl -s https://get.nextflow.io | bash
    echo 'alias nextflow='$(realpath nextflow) >> ~/.bashrc
    source ~/.bashrc
    ```
6. Pull github repo:
    ```
    git clone https://github.com/SowpatiLab/ONT_Methylation_Benchmarking.git 
    cd ONT_Methylation_Benchmarking
    ```
7. Index reference files
    All the reference files are expected to be indexed first.
    ```
    samtools faidx example/references/H.pylori_J99_ATCC700824.fa

    cut -f 1,2 \
        example/references/H.pylori_J99_ATCC700824.fa.fai \
        >  example/references/H.pylori_J99_ATCC700824.genome
    ```
    > **Note:** This is for the example reference file in the example folder. All other references need to be indexed in the same fashion.

8. Running the nextflow workflow:
    ```
    # change directory to example
    cd example

    # run nextflow with conda 
    nextflow run ../benchmark_nextflow \
        -params-file config.yaml \
        -profile conda --conda_prefix $CONDA_PREFIX \
        --threads 10 \
        --memory  32.GB

    # running with docker profile
    # only run once 
    
    docker pull sowpati/ont-methylation-benchmarking:latest

    [ ! -d tooling/rockfish_models ] && mkdir -p tooling/rockfish_models
    docker run -v $(pwd):$(pwd) -w $(pwd) \
        sowpati/ont-methylation-benchmarking:latest rockfish download \
            -m 5kHz -s tooling/rockfish_models

    # run nextflow with docker
    nextflow run ../benchmark_nextflow \
        -params-file config.yaml \
        -profile docker \
        --threads 10 \
        --memory  32.GB

    # run nextflow with apptainer
    nextflow run ../benchmark_nextflow \
        -params-file config.yaml \
        -profile apptainer \
        --threads 10 \
        --memory  32.GB
    ```
9. Installing [Snakemake](https://snakemake.readthedocs.io/en/stable/)
    ```
    # option 1:
    conda create \
        -c conda-forge \
        -c bioconda -c nodefaults \
        -n benchmark_env snakemake

    # option 2:
    conda env create \
        -n benchmark_env \
        -f benchmark_nextflow/envs/benchmarking_env.yml
    
    # activate conda env
    conda activate benchmark_env
    ```

10. Running the snakemake workflow:
    ```
    ## ensure snakemake is installed 
    snakemake --use-apptainer \
        ../benchmark_snakemake/snakefile \
        --cores 10
    ```

## Final folder structure 
<pre>
.
├── benchmark_nextflow         # nextflow  workflow lives here
├── benchmark_snakemake        # snakemake workflow lives here
├── output
|   │   ├── bam                # bam files go here
|   │   ├── sorted_mod               # mod bams
|   │   ├── sorted_mod_cleansed      # filtered mod bams
|   │   ├── sorted_move              # move table bams
|   │   ├── sorted_move_cleansed     # filtered move table bams
|   │   └── sorted_move_fnord        # move table bams sorted by pod5 id
│   ├── intermediary
|   │   ├── blow5
|   │   └── fastq
│   ├── meta                  # final output beds for each tool
|   │   ├── deepbam
|   │   ├── deepmod2
|   │   ├── deepplant
|   │   ├── dorado
|   │   ├── f5c
|   │   ├── f5c_stranded
|   │   └── rockfish
│   ├── qc
|   │   ├── mosdepth
|   │   ├── nanoplot
|   │   ├── nanoq
|   │   └── nanostat
│   └── tool_out
|       ├── deepbam
|       ├── deepmod2
|       ├── deepplant
|       ├── dorado
|       ├── f5c
|       └── rockfish
├── pod5                       # input raw signal files
├── references                 # references files go here
├── tooling                    # tool install dir
│   ├── DeepBAM_models
│   ├── deepmod2
│   ├── DeepPlant_models
│   ├── dorado
│   ├── dorado_models
│   ├── f5c
│   ├── modkit
│   ├── rockfish
│   └── rockfishmodels
├── config.yaml                # controls for the workflow
├── references.yaml            # reference file map
└── work                       # working folder generated by nextflow
</pre>

> **Note:** For more detailed usage of the workflow refer [ONT_Methylation_Benchmarking](https://github.com/SowpatiLab/ONT_Methylation_Benchmarking/blob/main/README.md) GitHub repository.
