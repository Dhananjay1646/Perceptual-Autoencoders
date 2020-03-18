# Perceptual-Autoencoders
Implementation of [Improving Image Autoencoder Embeddings with Perceptual Loss](https://arxiv.org/abs/2001.03444) and [Pretraining Image Encoders without Reconstruction via Feature Prediction Loss](https://arxiv.org/abs/2003.07441)

## Cite papers or repository

If you are using the repository or work as part of a scientific work you should cite the following paper:
```
@article{pihlgren2020improving,
    title={Improving Image Autoencoder Embeddings with Perceptual Loss},
    author={Gustav Grund Pihlgren and Fredrik Sandin and Marcus Liwicki},
    year={2020},
    journal={arXiv preprint arXiv:2001.03444},
}
```

If you are using anything from perceptual_embedder.py (i.e. FeaturePredictorCVAE, FeatureAutoencoder, PerceptualFeatureToImgCVAE, or FeatureToImgCVAE) you should also cite this paper:
```
@article{pihlgren2020pretraining,
    title={Pretraining Image Encoders without Reconstruction via Feature Prediction Loss},
    author={Gustav Grund Pihlgren and Fredrik Sandin and Marcus Liwicki},
    year={2020},
    journal={arXiv preprint arXiv:2003.07441},
}
```


## Requirements
The repository have been tested with Python 3.6 and 3.7, Pytorch 1.2.0, Torchvision 0.4.0, and SciPy 1.3.1

To use the OpenAI gym part of the repository (gym_datagenerator.py) you additionally need OpenAI gym with all its requirements for the desired gym environments as well as opencv-python (for cv2).
Since gym_datagenerator.py generates files that does not require OpenAI gym it can be run in an independent environment.
The repository have been tested with gym 0.14.0 and opencv-python 4.0.0.21

## Datasets
The repository have been setup to work with [STL-10](http://ai.stanford.edu/~acoates/stl10/) and [SVHN](http://ufldl.stanford.edu/housenumbers/) datasets as well as data generated with gym_datagenerator.py for the LunarLander-v2 environment.

The STL-10 binaries can be found here: http://ai.stanford.edu/~acoates/stl10/stl10_binary.tar.gz

The SVHN binaries can be found here: [train_32x32.mat](http://ufldl.stanford.edu/housenumbers/train_32x32.mat), [test_32x32.mat](http://ufldl.stanford.edu/housenumbers/test_32x32.mat), [extra_32x32.mat](http://ufldl.stanford.edu/housenumbers/extra_32x32.mat)

LunarLander-v2 data is generated by executing `python gym_datagenerator.py`. Rename the file to something suitable and rerun the command for as many datasets you need. Recommended is three (one for training autoencoders, one for training predictors, and one for testing) but if you're more concerned with time and memory than making a rigorous experiment you can use one file for all three purposes. You must then edit `experiment.py` by adding these files at their correct positions. Running `experiment.py` with the `--data lunarlander` flag will result in an error telling you what needs to be done unless the code has been edited properly.

The binaries (files containing the actual data) for all three datasets needs to be put in `datasets/LunarLander-v2`, `datasets/stl10`, and `datasets/svhn` respectively.

## Running experiments
To run experiments run `python experiment.py --data lunarlander|stl10|svhn`
The experiments can take many additional parameters which can be found by running `python experiment.py --help`
