![Screenshot](img/slim/guide_logo3.png) 
# Input Data


## LD Reference Data: 1000 Genomes 

BridgePRS estimates SNP-specific LD in the clumping step from an population target data in PLINK binary format.  By default, the main 
BridgePRS includes a sample LD reference panel (**BRIDGEDIR/data/1000G_sample**) for population super-groups **AFR** and **EUR** that is 
suitable for the [quick start tutorial](quikstart.md). 

A folder containing the full 1000 Genomes LD reference panel for populations **AFR**, **EUR**, **EAS**, **SAS**, and **AMR** can be downloaded 
[here](https://github.com/clivehoggart/BridgePRS/archive/refs/heads/main.zip) and unzipped into **BRIDGEDIR/data/1000G_ref** to enable full usage 
of BridgePRS. 

To run BridgePRS using a custom LD reference please see [customization](guide_customization.md). 





## Trait Data: GWAS Sumstats and Phenotype Data

**Target Data** 

For the target population (where the trait is being estimated) BridgePRS requires GWAS summary stats
and two phenotype files (for test and validation): 




|Name|Command Line flag|Required|Description|
|:-:|:-:|:-:|:-:|
|Sumstats|--sumstats_prefix|Yes|GWAS Summary Statsd|
|Phenotypes|--phenotype_files|Target Pop Only|Test And Validation Phenotype Files|
|Snp List|--snp_file|No|List QCed SNP ids| 

!!! tip "Creating a Configuration File"
    The following command will validate the input data supplied on the command line 
    ```
    ./bridgePRS check data -o out --pop AFR 
                           --sumstats_prefix data/pop_africa/sumstats/afr.chr
                           --phenotype_files data/pop_africa/phenotypes/afr_test.dat data/pop_africa/phenotypes/afr_validation.dat
    ```
    And produce a configuration file for an african population that mirrors the supplied configuration file: 
    === "$ cat data/afr_cont.config"
    ```R
     ....
     POP=AFR
     SUMSTATS_PREFIX=pop_africa/sumstats/afr.chr
     PHENOTYPE_FILES=pop_africa/phenotypes/afr_test.dat,pop_africa/phenotypes/afr_validation.dat
     SNP_FILE=pop_africa/snps.txt
    ```

**Model Population** 

For the model population (used to produce prior distributions) BridgePRS requries GWAS summary stats 
and one phenotype file (if available).  If it is not available then the test file 
from the target population can be substituted, as shown in the two configuration files: 


=== "With Phenotype Data"

    ```R
    POP=EUR 
    SUMSTATS_PREFIX=pop_europe/sumstats/eur.chr
    PHENOTYPE_FILES=pop_europe/phenotypes/eur_test.dat
    SNP_FILE=pop_europe/snps.txt
    ```

=== "Without Phenotype Data"

    ```R
    POP=EUR
    SUMSTATS_PREFIX=pop_europe/sumstats/eur.chr
    PHENOTYPE_FILES=pop_africa/phenotypes/afr_test.dat
    SNP_FILE=pop_europe/snps.txt
    ```



## File Specifications 


### 1) Sumstats Data 

GWAS summary statistics can be provided using a prefix to multiple chromosome separated files with the `--sumstats_prefix` flag or 
with using a single sumstats file with the `--sumstats_file` flag.  If a prefix is given, then a suffix can be provided as well `--sumstats_suffix`. 
GWAS summary statistics must be provided as a whitespace delimited file containing association analysis results for SNPs on the base phenotype.
BridgePRS has no problem reading in a gzipped base file (need to have a **.gz** suffix) or splitting the file by chromosome if necessary.  
An example of a sumstats file with default column headers is shown: 

|#CHROM|POS|ID|REF|ALT|A1|A1_FREQ|TEST|OBS_CT|BETA|SE|T_STAT|P|ERRCODE|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|1|754105|rs12184325|T|C|G|0.0257573|ADD|4853|0.820864|0.413692|1.98424|0.0472871|.|
|1|840753|rs4970382|C|T|G|0.483495|ADD|4847|0.0011142|0.128347|0.00868116|0.993074|.|
|1|958905|rs2710890|G|A|G|0.424387|ADD|4814|0.108094|0.132225|0.817497|0.413687|.|

Column headers can be specified on the command line or in a configuration file using `--ssf` flags: 
(`--ssf-chr`,`--ssf-p`, `--ssf-snpid`, `--ssf-se`, `--ssf-ss`, `--ssf-beta`, `--ssf-ref`, `--ssf-alt`, `--ssf-maf`.)


|Flag|--ssf-chr|--ssf-snpid|--ssf-ref|--ssf-alt|--ssf-maf|--ssf-ss|--ssf-beta|--ssf-se|--ssf-p|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|Default|#CHROM|ID|REF|A1|A1_FREQ|OBS_CT|BETA|SE|P|


### 2) Phenotype Files
Phenotype files can be provided to BridgePRS using the `--phenotype_files` flag. 
This must be a tab / space delimited file and missing data **must** be represented by either `NA` or `-9` (only for binary traits).
The first two column of the phenotype file should be the FID and the IID, and the rest can be phenotypes/covariates:  

|FID|IID|y|y.binary|PC1|PC2|
|:-:|:-:|:-:|:-:|:-:|:-:| 
|afr1_1|afr2_1|24.4|1|0.53|0.950| 
|afr1_2|afr2_2|4.10|0|0.59|0.450| 
|afr1_3|afr2_3|37.2|1|0.73|-0.13| 
|afr1_4|afr2_4|5.40|0|0.44|-0.55| 


The phenotype of interest can be specified with the `--phenotype` flag and the covariates can be given as a comma separated list 
after the `--covariates` flag: 

    ```
    ./bridgePRS check data -o out --pop AFR --phenotype y --covariates PC1,PC2 
                           --phenotype_files data/pop_africa/phenotypes/afr_test.dat data/pop_africa/phenotypes/afr_validation.dat
    ```

!!! Warning
    The column name(s) should not contain *space* nor *comma*


### 3) QC SNP List 
To select only SNPS that have passed QC, you can provide a file using the `--snp_file` flag. 





