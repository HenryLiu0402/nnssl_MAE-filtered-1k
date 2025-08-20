# nnssl_MAE-filtered-1k
NTUST_EE304 @SSL3D Challenge
Primus-M network architecture

## Description
...

## Environment
**GPU:** NVIDIA RTX A6000 (NVIDIA TITAN RTX)  
**RAM:** 128G (64G)  
**Python:** 3.10.12  
**CUDA:** 12.4  
**PyTorch:** 2.6.0+cu124  

## Pretraining Strategy
...

## Hyperparameter Settings 
batch_size = 4  
initial_lr = 1e-2  
patch_size = (160, 160, 160)  
mask ratio: 0.75  
num_epochs = 500  
filtered modalities: "T1w", "inplainT1", "MP2RAGE", "FLAIR", "T2w", "inplainT2", "ADC", "DWI"

## Example

```bash
#set environment variables
export nnssl_raw=/NFS/dataset/openmind/OpenMind/nnssl_raw
export nnssl_preprocessed=/NFS/dataset/openmind/OpenMind/nnssl_preprocessed
export nnssl_results=/NFS/dataset/openmind/OpenMind/nnssl_results
echo $nnssl_raw
echo $nnssl_preprocessed
echo $nnssl_results

#Preprocessing the data
 # >> same process as nnssl "Preprocessing the data"

# MAE pretraining (filtered dataset)
nnssl_train 745 onemmiso -tr BaseMAETrainer_BS4_filtered_1000ep -p nnsslPlans
```

## License
This project is based on [nnssl (MIC-DKFZ)](https://github.com/MIC-DKFZ/nnssl)
and distributed under the [Apache License 2.0](LICENSE).
