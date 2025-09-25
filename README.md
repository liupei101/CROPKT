# CROPKT: Cross-Cancer Knowledge Transfer in WSI-based Prognosis Prediction

[[Paper]](https://arxiv.org/abs/2508.13482) | [[UNI2-h-DSS Dataset]](https://huggingface.co/datasets/yuukilp/UNI2-h-DSS) | [[Acknowledgements]](https://github.com/liupei101/CROPKT?tab=readme-ov-file#acknowledgements) | [[Citation]](https://github.com/liupei101/CROPKT?tab=readme-ov-file#-citation)

**Abstract**: Whole-Slide Image (WSI) is an important tool for estimating cancer prognosis. Current studies generally follow a conventional cancer-specific paradigm where one cancer corresponds to one model. However, it naturally struggles to scale to rare tumors and cannot utilize the knowledge of other cancers. Although a multi-task learning-like framework has been studied recently, it usually has high demands on computational resources and needs considerable costs in iterative training on ultra-large multi-cancer WSI datasets. To this end, this paper makes a paradigm shift to knowledge transfer and presents the first preliminary yet systematic study on **cross-cancer prognosis knowledge transfer in WSIs**, called **CROPKT**. It has three major parts: (*i*) we curate a large dataset (UNI2-h-DSS) with 26 cancers and use it to measure the transferability of WSI-based prognostic knowledge across different cancers (including rare tumors); (*ii*) beyond a simple evaluation merely for benchmark, we design a range of experiments to gain deeper insights into the underlying mechanism of transferability; (*iii*) we further show the utility of cross-cancer knowledge transfer, by proposing a routing-based baseline approach (ROUPKT) that could often efficiently utilize the knowledge transferred from off-the-shelf models of other cancers. We hope CROPKT could serve as an inception and lay the foundation for this nascent paradigm, i.e., WSI-based prognosis prediction with cross-cancer knowledge transfer.

---

*On updating. Stay tuned.*

📚 Recent updates:
- 25/09/25: created a repo for CROPKT

## 👩‍💻 Running Code

### Pre-requisites

All experiments are run on a machine with
- two NVIDIA GeForce RTX 3090 GPUs
- python 3.8 and pytorch==1.11.0+cu113

Detailed package requirements:
- for `pip` or `conda` users, full requirements are provided in [requirements.txt](https://github.com/liupei101/CROPKT/blob/main/requirements.txt).
- for `Docker` users, you could use our base Docker image via `docker pull yuukilp/deepath:py38-torch1.11.0-cuda11.3-cudnn8-devel` and then install additional essential python packages (see [requirements.txt](https://github.com/liupei101/CROPKT/blob/main/requirements.txt)) in the container.

### Training Models 

Use the following command to load a experimental configuration and then train & evaluate a survival model (based on 5-fold cross-validation):
```bash
python3 main.py --config config/cfg_sa_base_uni2h_stl_moe_pkt.yaml --handler SAT --multi_run
```

All important configurations are explained in `config/cfg_sa_base_uni2h_stl_moe_pkt.yaml`. 

For training & evaluating traditional cancer-specific survival models, use the following:
```bash
python3 main.py --config config/cfg_sa_base_uni2h_stl.yaml --handler SA --multi_run
```

## Training Logs

We advocate open-source research and would like to make our training logs publicly-available. Full training logs in this study can be accessed at [Google Drive](https://drive.google.com/drive/folders/1jWUm82pYnuIc1ova_qHqb0bFx1hjs_1G?usp=sharing).

## UNI2-h-DSS Dataset

HF Dataset (with complete DSS labels): https://huggingface.co/datasets/yuukilp/UNI2-h-DSS

## Acknowledgements

We thank the following great works that contribute to this work:

- [UNI](https://github.com/mahmoodlab/UNI): a state-of-the-art foundation model for pathology; it is used to extract patch features from WSIs.
- [UNI2-h features](https://huggingface.co/datasets/MahmoodLab/UNI2-h-features): the datasets for this study are derived from it.
- [TCGA GDC Data portal](https://portal.gdc.cancer.gov/): it provides the source data for analysis.

## 📝 Citation

If you find this work helps your research, please consider citing our paper:
```txt
@misc{liu2025cropkt,
      title={Cross-Cancer Knowledge Transfer in WSI-based Prognosis Prediction}, 
      author={Pei Liu and Luping Ji and Jiaxiang Gou and Xiangxiang Zeng},
      year={2025},
      eprint={2508.13482},
      archivePrefix={arXiv},
      url={https://arxiv.org/abs/2508.13482}, 
}
```