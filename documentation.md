# ONT Methylation Benchmarking Datasets

This data source contains the datasets that were used for benchmarking various tools and models for Oxford Nanopore (ONT) sequencing based identification of DNA methylation

## Data Access

You can access the following data through the AWS Open Data Registry:
- Raw files (pod5)
- Basecalled with move table files (bam) 
- Modified basecalled files with alignment (modbam)
- Processed data for methylation calling (modbed)
- Reference files (fasta)
- Annotation files (gtf/gff)

## ONT Datasets
<!-- 
|Group|Dataset|samples|chemistry|sample rate|basecall model|
|-----|-------|-------|---------|-----------|--------------|
|Mammals| Human HG002<br/> Mouse Brain<br/> Mouse ESC<br/> Mouse Brain| Native (WT)<br/>Native (WT)<br/>Native (WT)<br/>Native (WT)<br/> | R10.4.1<br/>R10.4.1<br/>R10.4.1<br/>R10.4.1 | 4kHz<br/>5kHz<br/>5kHz<br/>5kHz<br/> | v4.0.1 sup<br/>v5.0.0 sup<br/>v5.0.0 sup<br/>v5.0.0 sup |
| Plants | <i>Oryza sativa</i><br/><i>Arabidopsis thaliana</i> | Native (WT)<br/>Native (WT) | R10.4.1<br/>R10.4.1<br/> | 5kHz<br/>5kHz<br/> | v5.0.0 sup<br/>v5.0.0 sup |
| Bacteria |‎<br/><i>Escherichia coli</i> str. K-12 substr. MG1655‎<br/>‎<br/><hr><i>Helicobacter pylori</i> str. 26695<br/>‎<br/><hr/><i>Helicobacter pylori</i> str. J99<br/> <hr/><i>Anabaena variabilis</i> ATCC 27983<br/><hr/><i>Treponema denticola</i> ATCC 35405<br/> | Native (WT) <br/>Double Mutant (DM) <br/>Double Mutant M.SssI Treated (DM_MSssI) <br/><hr/>Native (WT) <br/>Whole Genome Amplified (WGA) <br/><hr/>Native (WT) <br/><hr/>Native (WT) <br/><hr/>Native (WT) <br/> |‎<br/>R10.4.1<br/>R10.4.1<br/>R10.4.1<br/>‎<br/><hr/>R10.4.1<br/>‎<br/><hr/>>R10.4.1<br/><hr/>R10.4.1<br/><hr/>R10.4.1<br/><hr/>R10.4.1<hr/>
 -->

<table>
    <thead>
        <tr>
            <th scope="col" rowspan="1"> Group </th>
            <th scope="col" rowspan="1"> Dataset </th>
            <th scope="col" rowspan="1"> samples </th>
            <th scope="col" rowspan="1"> chemistry </th>
            <th scope="col" rowspan="1"> sample rate </th>
            <th scope="col" rowspan="1"> Basecall Model </th>
        </tr>
    </thead>
    <tbody>
        <tr>
           <td rowspan="3">Mammals</td>
           <td>Human HG002</td>
           <td>Native (WT)</td>
           <td>R10.4.1</td>
           <td>4kHz</td>
           <td>v4.0.1 sup</td>
        </tr>
        <tr>
           <td>Mouse Brain</td>
           <td>Native (WT)</td>
           <td>R10.4.1</td>
           <td>5kHz</td>
           <td>v5.0.0 sup</td>
        </tr>
        <tr>
           <td>Mouse ESC</td>
           <td>Native (WT)</td>
           <td>R10.4.1</td>
           <td>5kHz</td>
           <td>v5.0.0 sup</td>
        </tr>
        <tr>
           <td rowspan="2">Plant</td>
           <td><i>Oryza sativa</i></td>
           <td>Native (WT)</td>
           <td>R10.4.1</td>
           <td>5kHz</td>
           <td>v5.0.0 sup</td>
        </tr>
        <tr>
           <td><i>Arabidopsis thaliana</i></td>
           <td>Native (WT)</td>
           <td>R10.4.1</td>
           <td>5kHz</td>
           <td>v5.0.0 sup</td>
        </tr>
        <tr>
           <td rowspan="8">Bacteria</td>
           <td rowspan="3"><i>Escherichia coli str. K-12 substr. MG1655</i></td>
           <td>Native (WT)</td>
           <td>R10.4.1</td>
           <td>5kHz</td>
           <td>v5.0.0 sup</td>
        </tr>
        <tr>
           <td>Double Mutant (DM)</td>
           <td>R10.4.1</td>
           <td>5kHz</td>
           <td>v5.0.0 sup</td>
        </tr>
        <tr>
           <td>Double Mutant M.SssI Treated (DM_MSssI)</td>
           <td>R10.4.1</td>
           <td>5kHz</td>
           <td>v5.0.0 sup</td>
        </tr>
        <tr>
           <td rowspan="2"><i>Helicobacter pylori str. 26695</i></td>
           <td>Native (WT)</td>
           <td>R10.4.1</td>
           <td>5kHz</td>
           <td>v5.0.0 sup</td>
        </tr>
        <tr>
           <td>Whole Genome Amplified (WGA)</td>
           <td>R10.4.1</td>
           <td>5kHz</td>
           <td>v5.0.0 sup</td>
        </tr>
        <tr>
           <td><i>Helicobacter pylori str. J99</i></td>
           <td>Native (WT)</td>
           <td>R10.4.1</td>
           <td>5kHz</td>
           <td>v5.0.0 sup</td>
        </tr>
        <tr>
           <td><i>Anabaena variabilis ATCC 27983</i></td>
           <td>Native (WT)</td>
           <td>R10.4.1</td>
           <td>5kHz</td>
           <td>v5.0.0 sup</td>
        </tr>
        <tr>
           <td><i>Treponema denticola ATCC 35405</i></td>
           <td>Native (WT)</td>
           <td>R10.4.1</td>
           <td>5kHz</td>
           <td>v5.0.0 sup</td>
        </tr>
    </tbody>
</table>

## EMSeq Datasets
<table>
    <thead>
        <tr>
            <th>Group</th>
            <th>Dataset</th>
            <th>Samples</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan="3">Mammals</td>
            <td>Human HG002</td>
            <td>hg38.fa.gz</td>
        </tr>
        <tr>
            <td>Mouse Brain</td>
            <td>Native (WT)</td>
        </tr>
        <tr>
            <td>Mouse ESC</td>
            <td>Native (WT)</td>
        </tr>
        <tr>
            <td rowspan="2">Plants</td>
            <td><i>Oryza sativa</i></td>
            <td>Native (WT)</td>
        </tr>
        <tr>
            <td><i>Arabidopsis thaliana</i></td>
            <td>Native (WT)</td>
        </tr>
        <tr>
            <td rowspan="5">Bacteria</td>
            <td rowspan="3"><i>Escherichia coli str. K-12 substr. MG1655</i></td>
            <td>Native (WT) <br/>Double Mutant (DM)<br/>Double Mutant M.SssI Treated (DM_MSssI)</td>
        </tr>
    </tbody>
</table>

## Reference files

<table>
    <thead>
        <tr>
            <th>Group</th>
            <th>Dataset</th>
            <th>Reference file</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan="3">Mammals</td>
            <td>Human HG002</td>
            <td>hg38.fa.gz</td>
        </tr>
        <tr>
            <td>Mouse Brain</td>
            <td>mm39.fa.gz</td>
        </tr>
        <tr>
            <td>Mouse ESC</td>
            <td>mm39.fa.gz</td>
        </tr>
        <tr>
            <td rowspan="2">Plants</td>
            <td><i>Oryza sativa</i></td>
            <td>osativa.fa.gz</td>
        </tr>
        <tr>
            <td><i>Arabidopsis thaliana</i></td>
            <td>arabidopsis.fa.gz</td>
        </tr>
        <tr>
            <td rowspan="5">Bacteria</td>
            <td><i>Escherichia coli str. K-12 substr. MG1655</i></td>
            <td>ecoli.fa.gz</td>
        </tr>
        <tr>
            <td><i>Helicobacter pylori str. 26695</i></td>
            <td>hpylori_26695.fa.gz</td>
        </tr>
        <tr>
            <td><i>Helicobacter pylori str. J99</i></td>
            <td>hpylori_J99.fa.gz</td>
        </tr>
        <tr>
            <td><i>Anabaena variabilis ATCC 27983</i></td>
            <td>avariabilis.fa.gz</td>
        </tr>
        <tr>
            <td><i>Treponema denticola ATCC 35405</i></td>
            <td>tdenticola.fa.gz</td>
        </tr>
    </tbody>
</table>


## Use of ONT methylation datasets
- Assessment and reproduction of benchmarking studies
- Development of tools and methods for methylation calling using ONT data
- Example dataset for testing methylation analysis pipelines

## Release Note & Updates
<b>Version Number</b>: V0.1<br/>
<b>Date</b>: 2025-09-30
Initial release of the methylation benchmarking data on AWS. Includes raw nanopore files and methylation analysis files
