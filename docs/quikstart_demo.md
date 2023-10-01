![Screenshot](img/slim/quikstart_logo2.png)


## Configuration Files 

The target and model [configuration files](guide_input.md) used in this tutorial point to all the files required to 
run BridgePRS:  
 
=== "target: data/afr.config"

    ```R
    POP=AFR
    LDPOP=AFR
    SUMSTATS_PREFIX=pop_africa/sumstats/eur.chr
    GENOTYPE_PREFIX=pop_africa/genotypes/afr_genotypes
    PHENOTYPE_FILES=pop_africa/phenotypes/afr_test.dat,pop_africa/phenotypes/afr_validation.dat
    SNP_FILE=pop_europe/snps.txt
    ```

=== "model: data/eur.config"

    ```R
    POP=EUR
    LDPOP=EUR
    SNP_FILE=pop_europe/snps.txt
    SUMSTATS_PREFIX=pop_europe/sumstats/eur.chr
    GENOTYPE_PREFIX=pop_europe/genotypes/eur_genotypes
    PHENOTYPE_FILES=pop_europe/phenotypes/eur_test.dat
    ```

The phenotype files include two variables (**"y"** and **"y.binary"**) used in the tutorial.  



=== "$ head -n1 pop_africa/phenotypes/afr_test.dat" 

    ```R
    .
    FID IID y y.binary
    ```


## Demo 1: Continuous Trait [ "y" ] 

!!! tips "Easyrun Command" 
     Run BridgePRS on the toy phenotype "y" with the following command: 
        ```
        ./bridgePRS easyrun go -o out1 --pop_configs data/afr.config data/eur.config --phenotype y 
        ```

And verify that the summary figure `out1/bridgeSummary.png` is created: 

![Screenshot](img/combo1.png)


## Demo 2: Binary Trait [ "y.binary" ] 

Next make sure you are able to repeat the process with a binary phenotype. 



!!! tips "Easyrun Command" 
    Run BridgePRS on the toy binary phenotype "y.binary" with the following command: 
        ```
        ./bridgePRS easyrun go -o out2 --pop_configs data/afr.config data/eur.config --phenotype y.binary
        ```

## Next Up:

On the page we will discuss the results that bridgePRS generates and on the following page we will include 
two challenge problems to make sure your expertise at bridgePRS is peak level. 

    


