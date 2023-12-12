## CLIP-Dissect

An automatic and efficient tool to describe functionalities of individual neurons in DNNs.

This is the official repository for our paper: [CLIP-Dissect: Automatic Description of Neuron Representations in Deep Vision Networks](https://arxiv.org/abs/2204.10965) published at ICLR 2023. 

**Update 6/5/23**: We have conducted a crowdsourced evaluation of our description quality, results are available on [arxiv](https://arxiv.org/abs/2204.10965) (Appendix B).

![Overview](data/github_overview_figure.png)

## Installation

1. Install Python (3.10)
1. Install Pytorch (tested with 1.12.0, also works with 2.0) and Torchvision >= 0.13 following instructions from https://pytorch.org/get-started/previous-versions/
3. Install remaining requirements using `conda env create --file environment.yaml`
4. Download the Broden dataset (images only) using `bash dlbroden.sh`
5. (Optional) Download ResNet-18 pretrained on Places-365: `bash dlzoo_example.sh`

We do not provide download instructions for ImageNet data, to evaluate using your own copy of ImageNet validation set you must set 
the correct path in `DATASET_ROOTS["imagenet_val"]` variable in `data_utils.py`.



## Recreating experiments

To label neurons, I used labelling.ipynb. To analyze data the I got from labelling, I used data_analysis.ipynh.


## Sources:

- CLIP: https://github.com/openai/CLIP
- Text datasets(10k and 20k): https://github.com/first20hours/google-10000-english
- Text dataset(3k): https://www.ef.edu/english-resources/english-vocabulary/top-3000-words/
- Broden download script based on: https://github.com/CSAILVision/NetDissect-Lite

## Common errors

**Incorrect activations cached:**

The code automatically caches the saved activations of target model and CLIP in `saved_activations`, and if a file already exists with the same save name the code will load these activations instead of recalculating. However sometimes you may wish to modify the pipeline in a way that doesn't change the name of the saved activations and want to recalculate the activations. In this case you need to manually delete the relevant files from saved_activations before rerunning CLIP-Dissect, as using incorrect activations will give incorrect results.

## Cite this work

T. Oikarinen and T.-W. Weng, CLIP-Dissect: Automatic Description of Neuron Representations in Deep Vision Networks, ICLR 2023.

```
@article{oikarinen2023clip,
  title={CLIP-Dissect: Automatic Description of Neuron Representations in Deep Vision Networks},
  author={Oikarinen, Tuomas and Weng, Tsui-Wei},
  journal={International Conference on Learning Representations},
  year={2023}
}
```
