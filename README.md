# Voice Conversion Using StarGAN

## Introduction

This work aims to conduct voice conversion (VC) between a Japanese speaker and a Chinese speaker. We achieve this by using [StarGAN-VC](https://arxiv.org/abs/1806.02169).

## Dependencies

- Python 3.6+
- pytorch 1.0
- librosa
- pyworld
- tensorboardX (Optional)
- scikit-learn


## Dataset

### Basic Information

The dataset looks like this:

```
data
├───speakers
│   ├───p1
│   └───p2
└───speakers_test
    ├───p1
    └───p2
```

The sample rate is **22050** for all wave files. There are 300 training examples of p1 and p2 respectively in the `speakers` directory and 10 testing examples of p1 and p2 respectively in the `speakers_test` directory. They are all chosen in a random fashion.

`p1` is the data of a Japanese speaker while `p2`  is Chinese. In our experiment, we consider `p2` as the source speaker and `p1` as the target speaker. In other words, we want `p2` to speak like `p1`.



### Japanese (private)

The Japanese data are extracted from the game [Yosuga no Sora]([Yosuga no Sora - Wikipedia](https://en.wikipedia.org/wiki/Yosuga_no_Sora)). The speaker, more precisely, the character is [Sora Kasugano]([Sora Kasugano | All Worlds Alliance Wiki | Fandom](https://all-worlds-alliance.fandom.com/wiki/Sora_Kasugano)). 

In consideration of intellectual rights, the Japanese dataset cannot be shared. However, you may collect your own data:)

### How to Collect Data?

- `*.xp3`: [Garbro](https://github.com/morkt/GARbro)
- `*.ks.scn` to `*.json`: [FreeMote](https://github.com/UlyssesWu/FreeMote)  
- `*.ogg` to `*.wav`: [ffmpeg](https://ffmpeg.org/)


### Chinese (public)

The Chinese dataset is [THCHS-30](http://www.openslr.org/18/), which is totally free!  




## Usage

### Preprocess

Extract features (mcep, f0, ap) from each speech clip. The features are stored as npy files. We also calculate the statistical characteristics for each speaker.

If you have  dataset that looks like ours and want to train your own VC model, you should do the preprocessing step.

```
python3 preprocess.py
```

This process may take minutes so if you are training on online servers (e.g. Colab), we recommend you download one to your local machine for next use:)



### Train

```
python3 main.py!
```



### Convert 

```
python3 main.py --mode test --test_iters 200000 --src_speaker p2 --trg_speaker p1
```



## Demo

[Colab demo](https://colab.research.google.com/drive/1R-Dc2AUAPFkcfkABUeejszfTeBgwdqZC?usp=sharing)



## References

[StarGAN-VC paper](https://arxiv.org/abs/1806.02169)

[Original code](https://github.com/hujinsen/pytorch-StarGAN-VC)

[Reference code](https://github.com/wubinary/DLHLP2020-SPRING)


## Acknowledgement

I should express my thanks to [CjangCjengh](https://github.com/CjangCjengh) for giving me both inspiration and advice.
