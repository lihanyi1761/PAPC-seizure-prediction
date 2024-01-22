# semi-supervised-seizure-prediction
EEG power spectra parameterization and adaptive channel selection towards efficient semi-supervised seizure prediction


This is code for the paper [EEG power spectra parameterization and adaptive channel selection towards efficient semi-supervised seizure prediction] which in the minor revision 


	@article{didilvlv,
	  title={EEG power spectra parameterization and adaptive channel selection towards efficient semi-supervised seizure prediction},
	  author={Hanyi Lia, Jiahui Liao, Hongxiao Wang, Chang’an A. Zhan and Feng Yang},
	  journal={computers in biology and medicine},
	  year={2024}
	}
 
#### Requirements

* tensorflow==2.6.2
* python==3.8.13
* numpy==1.19.5
* scipy==1.10.1
* six==1.15.0
* mn==1.4.0
* pywt==1.0.6
* stockwell==1.0.6


#### How to run the code
1. To obtain the channel selection results based on PAPC, please run the code below the file 'PAPC'

2. Set the paths in \*.json files. Copy files in folder "copy-to-CHBMIT" to your CHBMIT dataset folder.

3. Prepare preprocessed data for WGAN-GP training. A large storage is required.
```console
python3 main.py --mode save_STFT --dataset DATASET
```
* DATASET can be CHBMIT or siena-scalp-eeg-database-1.0.0.
* CHBMIT(https://physionet.org/content/chbmit/1.0.0/) and siena(https://physionet.org/content/siena-scalp-eeg/1.0.0/) are both common dataset which can be download.

4. Train  model. 
```console
python3 main.py --mode wgan-gp --dataset DATASET

```
* For comparison, MODEL can be dcgan,wgan,wgan_gp .

5. Leave-one-seizure-out cross-validation.
```console
python3 main.py --mode cvgan --dataset DATASET
```
