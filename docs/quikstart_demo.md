![Screenshot](img/slim/quikstart_logo2.png)



## Running Demo: 

Using the phenotype data identified in the previous step, both demo examples 
can be run using the "Easyrun" Command.  To run BridgePRS using a continuous phenotype: 

!!! tips "Easyrun Command: Continuous Trait (y)" 
     Run BridgePRS on the toy phenotype "y" with the following command: 
        ```
        ./bridgePRS easyrun go -o out1 --pop_configs data/afr.config data/eur.config --phenotype y 
        ```


And verify that a summary figure `out1/bridgeSummary.png` shown below is created.  Then repeat the 
process using a binary phenotype: 





!!! tips "Easyrun Command" 
    Run BridgePRS on the toy binary phenotype "y.binary" with the following command: 
        ```
        ./bridgePRS easyrun go -o out2 --pop_configs data/afr.config data/eur.config --phenotype y.binary
        ```

## Demo Results:


On the next page we will discuss the results that bridgePRS generates and on the following page we will include 
two challenge problems to make sure your expertise at bridgePRS is peak level. 

    
![Screenshot](img/combo1.png)



