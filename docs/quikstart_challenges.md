![Screenshot](img/slim/quikstart_logo4.png)


## Training

In the previous two examples the target population was a non-specific African (**AFR**) population 
and the model population  was European (**EUR**).  In these examples each population had a corresponding:  

- LD Reference Panel (Used for Clumping) 
- GWAS Summary Stats 
- Genotype/Phenotype Data 

This example may be unrealistic given real-world constraints and the realities of data sharing. 
Here we will consider will consider using BridgePRS in more realistic scenarios.  The data 
for these challenges is included in `data/challenges/`.

## Challenge 1: 

**I have access to genotype/phenotype data (<1000 samples, continuous phenotype) from a diverse population in Central Africa (data/challenges/CAF). 
I would like ot run PRS as accurately as possible, but my dataset is not large enough to conduct GWAS, however, I do have access to a moderately 
sized GWAS in a related West African population (1) and access to large-scale GWAS data from a European population (2).  How can I do this?**
 
**Available Data:** 

1. Related GWAS Moderately sized GWAS (**challenges/yoruba/sumstats/**) 
2. Large European GWAS (**challenges/UKB/sumstats/**) 
3. 1000G Reference Panel

Can you fill out the configuration files to carry this out? 

=== "Target Config File"

    ```R
    POP=
    LDPOP=
    SUMSTATS_PREFIX=
    GENOTYPE_PREFIX=caf/phenotypes/caf_genotypes
    PHENOTYPE_FILES=caf/phenotypes/caf_test.dat,pop_caf/phenotypes/caf_validation.dat
    ```

=== "[Answer]"

    ```R
    POP=CAF
    LDPOP=AFR 
    SUMSTATS_PREFIX=yoruba/sumstats/chr 
    GENOTYPE_PREFIX=caf/phenotypes/caf_genotypes
    PHENOTYPE_FILES=caf/phenotypes/caf_test.dat,pop_caf/phenotypes/caf_validation.dat
    ```

=== "Model Config FIle"

    ```R
    POP=
    LDPOP= 
    SUMSTATS_PREFIX=
    GENOTYPE_PREFIX=
    PHENOTYPE_FILES=
    ```

=== "Answer"

    ```R
    POP=EUR
    LDPOP=EUR
    SUMSTATS_PREFIX=ukb/sumstats/chr
    GENOTYPE_PREFIX=caf/phenotypes/caf_genotypes
    PHENOTYPE_FILES=caf/phenotypes/caf_test.dat
    ```




## Challenge 2: 

**I have access to GWAS data (1) and  genotype/phenotype (2) data (>2000 samples, binary phenotype) from a moderate sized population in Eastern Europe (data/challenges/UKR). 
I have reason to believe that this population has unique LD structure and would like to incorporate this into my model.  I also have GWAS and genotype/phenotype data from the UKB biobank 
that I wish to use to improve my results, how should I do this? 


1. Target GWAS     (**challenges/UKR/sumstats/**) 
2. Target Genotype/Phenotype Data  (**challenges/UKR/genotype/chr, challenges/UKR/phenotype.test,challenges/UKR/phenotype.valid**) 
3. Model European GWAS (**challenges/UKB/sumstats/**) 
4. Model Genotype/Phenotype Data  (**challenges/UKB/genotype/chr, challenges/UKB/phenotype.test**) 



=== "Target Config File"

    ```R
    POP=UKR
    LDPOP=
    SUMSTATS_PREFIX=
    GENOTYPE_PREFIX=ukr/phenotypes/ukr_genotypes
    PHENOTYPE_FILES=ukr/phenotypes/ukr_test.dat,pop_ukr/phenotypes/ukr_validation.dat
    ```

=== "[Answer]"

    ```R
    POP=ukr
    LDPOP=ukr*
    SUMSTATS_PREFIX=ukr/sumstats/chr 
    GENOTYPE_PREFIX=ukr/phenotypes/ukr_genotypes
    PHENOTYPE_FILES=ukr/phenotypes/ukr_test.dat,pop_ukr/phenotypes/ukr_validation.dat
    ```

=== "Model Config FIle"

    ```R
    POP=
    LDPOP= 
    SUMSTATS_PREFIX=
    GENOTYPE_PREFIX=
    PHENOTYPE_FILES=
    ```

=== "Answer"

    ```R
    POP=UKB
    LDPOP=EUR 
    SUMSTATS_PREFIX=ukb/sumstats/chr 
    GENOTYPE_PREFIX=ukb/phenotypes/ukr_genotypes
    PHENOTYPE_FILES=ukb/phenotypes/ukb_test.dat
    ```




  
















