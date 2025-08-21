# nnssl_MAE-filtered-1k
NTUST_EE304 @[SSL3D Challenge](https://ssl3d-challenge.dkfz.de/home)  
Primus-M network architecture

## Description
We evaluated different SSL strategies and dataset settings for the Primus-M track.
Our experiments included Masked Autoencoder (MAE) with both full and filtered datasets of varying sizes, as well as alternative SSL methods such as VoCo. 
In addition, we conducted extensive hyperparameter explorations (e.g., learning rates, batch sizes, masking ratios) to study their impact on model performance.  
Due to the time constraints of the competition, our best-performing approach is pure MAE with the filtered dataset


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
num_epochs = 1000  
filtered modalities: T1w, inplainT1, MP2RAGE, FLAIR, T2w, inplainT2, ADC, DWI

## Example

```bash
#set environment variables
export nnssl_raw=/NFS/dataset/openmind/OpenMind/nnssl_raw
export nnssl_preprocessed=/NFS/dataset/openmind/OpenMind/nnssl_preprocessed
export nnssl_results=/NFS/dataset/openmind/OpenMind/nnssl_results
#check if the environment variable is set
echo $nnssl_raw
echo $nnssl_preprocessed
echo $nnssl_results

#Preprocessing the data
 # >> same process as nnssl "Preprocessing the data"

# MAE pretraining (filtered dataset)
nnssl_train 745 onemmiso -tr BaseMAETrainer_BS4_filtered_1000ep -p nnsslPlans
```

## License
This project is based on [nnssl (MIC-DKFZ)](https://github.com/MIC-DKFZ/nnssl/tree/openneuro).  
It is licensed under the [Creative Commons Attribution-ShareAlike 4.0 International License](LICENSE).
