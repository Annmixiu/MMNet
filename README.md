# MTANet

## Introduction

The official implementation of "MTANET: Multi-band Time-frequency attention Network for Singing Melody Extraction from Polyphonic Music.

We propose a more powerful singing melody extractor named multi-band time-frequency attention network (MTANet) for polyphonic music. Experimental results show that our proposed MTANet achieves promising performance compared with existing state-of-the-art methods, while keeping with a small number of network parameters.

<p align="center">
<img src="fig/arch.png" align="center" alt="MTANet Architecture" width="100%"/>
</p>

## Important updata
### 2023. 03. 19

(i) Due to the author's mistake, Figure 3 in the manuscript of the paper shows an earlier version, which may cause some misunderstandings for reviewers and readers. I am very sorry for this situation! The following picture is the revised version for reference and I will make formal corrections in the subsequent manuscript.

<p align="center">
<img src="fig/Figure3.png" align="center" alt="Hourglass sub-network" width="85%"/>
</p>

(ii) Rename the MMNet to the MTANet.

### 2023. 03. 20

The author has contacted the chairs and applied for modification. If the modification is successful, please ignore the above update. I am very sorry for the inconvenience to the reviewers and readers.

### 2023. 05. 20
The Paper has been accepted by INTERSPEECH 2023 and the official version awaits the official release.

The rest of the code will be sorted out and published soon.

### 2023. 06. 11
All the code is uploaded.

### 2023. 08. 19
When I read back the paper, I found a mistake witch is one of the dimension tracking descriptions in Figure 4. Specifically, the dimensions after concatenate operation are different for different stages. For example, the input feature size in the first MFA module is (B, 32, F, T), so the feature size after concatenate operation should be (B, 32+4×16, F, T). The difference is that the feature size after concatenate operation in the subsequent MFA modules is (B, 16+4×16, F, T) (i.e., B, (N+1)×C, F, T).

Although the original intention is to facilitate understanding and reading, but we ignored the strict relationship between the paper and the code. Since the paper can no longer be modified, it is very sorry for the troubles that bring readers here.

## Getting Started

### Download Datasets

* [MIR-1k](https://sites.google.com/site/unvoicedsoundseparation/mir-1k)
* [ADC 2004 & MIREX05](https://labrosa.ee.columbia.edu/projects/melody/)
* [MedleyDB](https://medleydb.weebly.com/)

After downloading the data, use the txt files in the data folder, and process the CFP feature by [feature_extraction.py](feature_extraction.py).

Note that the label data corresponding to the frame shift should be available before generation.

main.py is the main function of this project.
## Model implementation

Refer to the file: [mtanet.py](model/mtanet.py)

The replication code for other comparison models has been uploaded and can be found in the folder: [control group model](model/control%20group%20model).


## Result

### Prediction result

The visualization illustrates that our proposed MTANet can reduce the octave errors and the melody detection errors.

<p align="center">
<img src="fig/estimation1.png" align="center" alt="estimation1" width="50%"/>
</p>
<p align="center">
<img src="fig/estimation.png" align="center" alt="estimation" width="50%"/>
</p>

### Comprehensive result

The scores here are either taken from their respective papers or from the result implemented by us. Experimental results show that our proposed MTANet achieves promising performance compared with existing state-of-the-art methods.

<p align="center">
<img src="fig/Result.png" align="center" alt="Result" width="50%"/>
</p>

### Ablation study result

We conducted seven ablations to verify the effectiveness of each design in the proposed network. Due to the page limit, we selected the ADC2004 dataset for ablation study in the paper. More detailed results are presented here.

<p align="center">
<img src="fig/ablution_ADC2004.png" align="center" alt="ablution_ADC2004" width="50%"/>
</p>

<p align="center">
<img src="fig/ablution_MIREX 05.png" align="center" alt="ablution_MIREX 05" width="50%"/>
</p>

<p align="center">
<img src="fig/ablution_MEDLEY DB.png" align="center" alt="ablution_MEDLEY DB" width="50%"/>
</p>

## Download the pre-trained model

Refer to the contents of the folder: [pre-train model](pre-train%20model).

## Special thanks

* [Knut(Ke) Chen](https://github.com/RetroCirce)

* [Shuai Yu](https://github.com/yushuai)
