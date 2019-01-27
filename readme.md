## PixelCNN++

A Pytorch Implementation of [PixelCNN++.](https://arxiv.org/pdf/1701.05517.pdf)

Main work taken from the [official implementation](https://github.com/openai/pixel-cnn)

Pre-trained models are available [here](https://mega.nz/#F!W7IhST7R!PV7Pbet8Q07GxVLGnmQrZg)

I kept the code structure to facilitate comparison with the official code. 

The code achieves **2.95** BPD on test set, compared to **2.92** BPD on the official tensorflow implementation. 
<p align="center">
<img src="https://github.com/pclucas14/pixel-cnn-pp/blob/master/images/pcnn_lr:0.00020_nr-resnet5_nr-filters160_143.png">
<img src="https://github.com/pclucas14/pixel-cnn-pp/blob/master/images/pcnn_lr:0.00020_nr-resnet5_nr-filters160_122.png">
<img src="https://github.com/pclucas14/pixel-cnn-pp/blob/master/images/pcnn_lr:0.00020_nr-resnet5_nr-filters160_137.png">
<img src="https://github.com/pclucas14/pixel-cnn-pp/blob/master/images/pcnn_lr:0.00020_nr-resnet5_nr-filters160_101.png">
</p>

### Running the code
```
python main.py
```

### Differences with official implementation
1. No data dependant weight initialization 
2. No exponential moving average of past models for test set evalutation

### Contact
For questions / comments / requests, feel free to send me an email.\
Happy generative modelling :)

### Using PixelCNN++ in DEEPSEC
## Training your own model
To train your own PixelCNN++ model, run `main.py` and customize it according to the parameters of the codes.\
For example, to train a CIFAR10 model using default parameters, run `main.py` as follows:
```
python main.py --dataset cifar
```
For MNIST datasets, the command is 
```
python main.py --dataset mnist
```

## Loading pretrained model
The loading path of model's parameters is 
```DEEPSEC/Defenses/DefenseMethods/External/pixel_cnn_pp/models```
And the format of the parameter file is 
``` '{}_pixel_cnn.pth'.format(Dataset) ```.
For example, if you have trained a CIFAR10 model, you should rename the parameter file as `CIFAR10_pixel_cnn.pth`
and put it to ```DEEPSEC/Defenses/DefenseMethods/External/pixel_cnn_pp/models/```

## Configuring PixelCNN++ in DEEPSEC
As mentioned above, to use PixelCNN in DEEPSEC, this repo should be like:
```DEEPSEC/Defenses/DefenseMethods/External/pixel_cnn_pp```.
After putting your own model parameter files into the `models/` file, you can use PixelDefend utility supported in DEEPSEC!