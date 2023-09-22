
# Interpreting Results 

The easyrun command sequentially runs the [five subprograms](detail_commands.md) described in detail in our [here](detail_commands.md) and 
the output directory (eg. **out1** and **out2**): 

1. `prs-single:   `   Run PRS using the primary population only (AFR). 
2. `build-model:`     Estimate SNP weights & prior params from model pop (EUR). 
3. `prs-port:   `     Run target-PRS using the model snp weights. 
4. `prs-prior:`       Run target-PRS using model prior distributions. 
5. `analyze combine`  Combine results to produce a weighted target PRS result.

And produces output in the following five subdirectories: 

1. **prs-single_AFR/quantify/:** Weights/Predictions (*snp_weights.dat, *preds.dat) 
2. **model_EUR/prior:**          Model Priors 
3. **prs-port_AFR/quantify/:**   Weights/Predictions (*snp_weights.dat, *preds.dat) 
4. **prs-prior_AFR/quantify/:**  Weights/Predictions (*snp_weights.dat, *preds.dat) 
5. **prs-combined_AFR/:**        Weights/Predictions (*snp_weights.dat, *preds.dat) 


The directory structure created by this command is shown below: FR

![Screenshot](img/pipeline.png)

