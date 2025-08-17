# NetDPSyn: Synthesizing Network Traces under Differential Privacy

## Introduction

This repository contains code for the paper: NetDPSyn: Synthesizing Network Traces under Differential Privacy. NetDPSyn is the first system to synthesize high-fidelity network traces under privacy guarantees.

## Experimental setup

1. Download the raw datasets from [here](https://drive.google.com/drive/folders/1MHRJxLhnJWZln8XBCon9UrN_EwVj14BE). And save them in `./temp_data/raw_data/` folder.

2. Your directory structure should look like this:

        NetDPSyn
           └── temp_data
                   └── raw_data
                        └── caida.csv
                        └── cidds.csv
                        └── dc.csv
                        └── ton.csv
                        └── ugr16.csv
           └── exp
           └── ...

4. **Note:** Please ensure all paths in `config_dpsyn.py` are updated to reflect your local directory structure. Additionally, you can adjust parameters in `parameter_parser.py` as needed.


## Usage

1. **Preprocess Data**. Run `lib_preprocess/preprocess_network.py`. This will generate a preprocessed pickle file in the `temp_data/processed_data` folder, along with a mapping for binning. Additionally, a trivially decoded CSV file (binning and unbinning) will be created in the `temp_data/synthesized_records` folder.

        python preprocess_network.py


2. **Synthesize Data**. Next, run `main.py` to generate the synthesized data. The synthesized data will be saved in the `temp_data/synthesized_records` floder.

        python main.py


3. **Downstream Tasks**. You can run code from `lib_downstream` (e.g., `lib_downstream/ml_tasks.py`). This will print out the evaluation results for both the raw dataset and the synthesized dataset.

        python ml_tasks.py


## Citation
If you find our work useful for your research, please consider citing the paper: 
```
@inproceedings{10.1145/3646547.3689011,
author = {Sun, Danyu and Chen, Joann Qiongna and Gong, Chen and Wang, Tianhao and Li, Zhou},
title = {NetDPSyn: Synthesizing Network Traces under Differential Privacy},
year = {2024},
isbn = {9798400705922},
publisher = {Association for Computing Machinery},
address = {New York, NY, USA},
url = {https://doi.org/10.1145/3646547.3689011},
doi = {10.1145/3646547.3689011},
abstract = {As the utilization of network traces for the network measurement research becomes increasingly prevalent, concerns regarding privacy leakage from network traces have garnered the public's attention. To safeguard network traces, researchers have proposed the trace synthesis that retains the essential properties of the raw data. However, previous works also show that synthesis traces with generative models are vulnerable under linkage attacks.This paper introduces NetDPSyn, the first system to synthesize high-fidelity network traces under privacy guarantees. NetDPSyn is built with the Differential Privacy (DP) framework as its core, which is significantly different from prior works that apply DP when training the generative model. The experiments conducted on three flow and two packet datasets indicate that NetDPSyn achieves much better data utility in downstream tasks like anomaly detection. NetDPSyn is also 2.5 times faster than the other methods on average in data synthesis.},
booktitle = {Proceedings of the 2024 ACM on Internet Measurement Conference},
pages = {545–554},
numpages = {10},
keywords = {differential privacy, network flows, network packets, synthetic data generation},
location = {Madrid, Spain},
series = {IMC '24}
}
```


