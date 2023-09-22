

## 1) Preparation 


After [downloading](https://github.com/clivehoggart/BridgePRS/archive/refs/heads/main.zip) and unzipping BridgePRS 
into a suitable directory on your machine (referred to as `$BridgeDir`) you will observe the following file structure: 

=== "$ ls"

    
    ```R
     . 
     bridgePRS data/ src/ LICENSE README.md  
    ```

!!! tip "Using the terminal, type the following command from within the directory:" 
    ``` 
    $ chmod +x bridgePRS
    $ chmod +x src/Python/Xtra/plink*
    ``` 
    to make bridgePRS and plink executable 


!!! warning "Extra MacOs Security:" 
    MacOs often block executables if they are not approved from the app store.
 
    You may have to change your settings to allow Plink to be called 

## 2) Requirements 

Next, confirm that the required libraries and binaries are installed and available by the instructions in [Requirements.](detail_requirements.md) 
Alternatively, you can type: 
=== "$./bridgePRS check requirements"  
and bridgePRS to check your system and prompt/direct you to install any missing dependencies. 

## 3) Toy Data

This tutorial uses the sample [configuration files](detail_input.md) located in the **data** directory:   

- A primary (smaller sample size) population (**data/afr.config**) of "AFR" ancestry.  
- A model (larger sample size) population (**data/eur.config**) of "EUR" ancestry. 


For more information on configuration files, see [Input Data](detail_input.md).






