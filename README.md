## Super Resolution
### Superresolution using an efficient sub-pixel convolutional neural network

This example illustrates how to use the efficient sub-pixel convolution layer described in ["Real-Time Single Image and Video Super-Resolution Using an Efficient Sub-Pixel Convolutional Neural Network"](https://arxiv.org/abs/1609.05158) - Shi et al. for increasing spatial resolution within your network for tasks such as superresolution.

```
usage: main.py [-h] --upscale_factor UPSCALE_FACTOR [--batchSize BATCHSIZE]
               [--testBatchSize TESTBATCHSIZE] [--nEpochs NEPOCHS] [--lr LR]
               [--cuda] [--threads THREADS] [--seed SEED]

PyTorch Super Res Example

optional arguments:
  -h, --help            show this help message and exit
  --upscale_factor      super resolution upscale factor
  --batchSize           training batch size
  --testBatchSize       testing batch size
  --nEpochs             number of epochs to train for
  --lr                  Learning Rate. Default=0.01
  --cuda                use cuda
  --threads             number of threads for data loader to use Default=4
  --seed                random seed to use. Default=123

```

This example trains a super-resolution network on the [BSD300](https://www2.eecs.berkeley.edu/Research/Projects/CS/vision/bsds/) dataset, using crops from the 200 training images, and evaluating on crops of the 100 test images. A snapshot of the model after every epoch with filename `epoch_<epoch_number>.pth`

## Example Usage:

### Train

`python main.py --upscale_factor 3 --batchSize 4 --testBatchSize 100 --nEpochs 30 --lr 0.001 --cuda`

### Super Resolve

`python super_resolve.py --input_image dataset/BSDS300/images/test/16077.jpg --model weights/epoch_300.pth --output_filename out.png --cuda`

**Original image:**

![](assets/input.jpg)

**Super resolution:**

![](assets/out.png)
