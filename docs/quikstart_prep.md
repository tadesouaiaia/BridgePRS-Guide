![Screenshot](img/slim/quikstart_logo1.png)

## Preparation 


After [downloading](https://github.com/clivehoggart/BridgePRS/archive/refs/heads/main.zip) and unzipping BridgePRS 
into a suitable directory on your machine (referred to as `$BridgeDir`) you will observe the following file structure: 

=== "$ ls"

    
    ```R
     . 
     bridgePRS data/ src/ LICENSE README.md  
    ```

!!! tip "Using the terminal, type the following command from within the directory:" 
    ``` 
    chmod +x bridgePRS
    chmod +x src/Python/Xtra/plink*
    ``` 
    to make bridgePRS and plink executable 


## Requirements 

Next, confirm that the required libraries and dependencies are installed and available by following 
the instructions in [Requirements.](guide_requirements.md) 
Alternatively, you can type: 
=== "./bridgePRS check requirements -o out"  
and bridgePRS will check your system provide further instructions to help you install missing dependencies. 


!!! warning "Warning: Extra MacOs Security:" 
    If you see this msg when running 'check requirements' (or any other time): 
    ![Error](img/mac_plink.png)
    
    You will have to change your system settings to allow bridgePRS to call plink.  
    For instructions on how to do so, please click [here](mac_specific.md).  

## Sample Data

Once you have confirmed that your system is up to date and libraries are installed, you 
can locate the toy-data used in the demo.  Located in the **data** directory, these data 
is formatted as population [configuaration files](guide_input.md#the-configuration-file), 
that point to the files associated with the **target** and **base** populations being used to run bridgePRS: 


=== "target: data/afr.config"

    ```R
    POP=AFR
    LDPOP=AFR
    SUMSTATS_PREFIX=pop_africa/sumstats/eur.chr
    GENOTYPE_PREFIX=pop_africa/genotypes/afr_genotypes
    PHENOTYPE_FILE=pop_africa/phenotypes/afr_test.dat
    VALIDATION_FILE=pop_africa/phenotypes/afr_validation.dat
    SNP_FILE=pop_europe/snps.txt
    ```

=== "base: data/eur.config"

    ```R
    POP=EUR
    LDPOP=EUR
    SNP_FILE=pop_europe/snps.txt
    SUMSTATS_PREFIX=pop_europe/sumstats/eur.chr
    GENOTYPE_PREFIX=pop_europe/genotypes/eur_genotypes
    PHENOTYPE_FILES=pop_europe/phenotypes/eur_test.dat
    ```

Examining one the phenotype files pointed to by the configuration file, reveals the two variables (**"y"** and **"y.binary"**) used in the tutorial.  

=== "$ head -n1 pop_africa/phenotypes/afr_test.dat" 

    ```R
    .
    FID IID y y.binary
    ```

For more information on the configuration or phenotype filetype, see [Guide: Input Data](guide_input.md), 
or to run the tutorial demo go to the next page. 

