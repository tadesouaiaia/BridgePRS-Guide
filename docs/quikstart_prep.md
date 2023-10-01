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
can begin the tutorial using the sample data located in the **data** directory: 

    data/afr.config     #   A configuration file for a target population of African ancestry
    data/eur.config     #   A configuration file for a model population of European ancestry 
    

For more information on config files, see [Guide: Input Data](guide_input.md), or go to the next page. 


