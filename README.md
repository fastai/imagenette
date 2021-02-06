# Imagenette

> 🎶 *Imagenette, gentille imagenette,*
>
> *Imagenette, je te plumerai.* 🎶
>
> (Imagenette theme song thanks to [Samuel Finlayson](https://twitter.com/IAmSamFin/status/1103737947004854272))

----

**NB:** 
- The Imagenette and Imagewoof datasets have recently (Dec 6 2019) changed. They now have a **70/30 train/valid** split. 
- The old versions (which have a much smaller validation set) are still available with the same URLs, but the URLs below point to the new versions. 
- We've also added the [new Image网 dataset](#image网) (see below for details). The leaderboards below been updated using the new datasets, using a strong. Can you beat it?...

----

## The Datasets

### Imagenette

Imagenette is a subset of 10 easily classified classes from Imagenet (tench, English springer, cassette player, chain saw, church, French horn, garbage truck, gas pump, golf ball, parachute).

'Imagenette' is pronounced just like 'Imagenet', except with a corny inauthentic French accent. If you've seen Peter Sellars in The Pink Panther, then think something like that. It's important to ham up the accent as much as possible, otherwise people might not be sure whether you're refering to "Imagenette" or "Imagenet". (*Note to native French speakers: to avoid confusion, be sure to use a corny inauthentic American accent when saying "Imagenet". Think something like the [philosophy restaurant skit](https://www.youtube.com/watch?v=oa0bCzwSNA0) from Monty Python's The Meaning of Life.*)

The '320 px' and '160 px' versions have their shortest side resized to that size, with their aspect ratio maintained.

- [Full size download](https://s3.amazonaws.com/fast-ai-imageclas/imagenette2.tgz)
- [320 px download](https://s3.amazonaws.com/fast-ai-imageclas/imagenette2-320.tgz)
- [160 px download](https://s3.amazonaws.com/fast-ai-imageclas/imagenette2-160.tgz).

Too easy for you? In that case, you might want to try [Imagewoof](#imagewoof).

### Imagewoof

Imagewoof is a subset of 10 classes from Imagenet that aren't so easy to classify, since they're all dog breeds. The breeds are: Australian terrier, Border terrier, Samoyed, Beagle, Shih-Tzu, English foxhound, Rhodesian ridgeback, Dingo, Golden retriever, Old English sheepdog. (No we will not enter in to any discussion in to whether a dingo is in fact a dog. Any suggestions to the contrary are un-Australian. Thank you for your cooperation.)

- [Full size download](https://s3.amazonaws.com/fast-ai-imageclas/imagewoof2.tgz); 
- [320 px download](https://s3.amazonaws.com/fast-ai-imageclas/imagewoof2-320.tgz); 
- [160 px download](https://s3.amazonaws.com/fast-ai-imageclas/imagewoof2-160.tgz). 

Imagewoof too easy for you too?!? Then get your hands on [Image网](#image网).

### Image网

Image网 is pronounced "Imagewang"; 网 means "net" in Chinese! Image网 contains Imagenette and Imagewoof combined, *but* with some twists that make it into a tricky semi-supervised unbalanced classification problem:

- The validation set is the same as Imagewoof (i.e. 30% of Imagewoof images); there are no Imagenette images in the validation set (they're all in the training set)
- Only 10% of Imagewoof images are in the training set!
- The remaining are in the `unsup` ("*unsupervised*") directory, and you *can not use their labels in training*!
- It's even hard to type and hard to say!

- [Full size download](https://s3.amazonaws.com/fast-ai-imageclas/imagewang.tgz); 
- [320 px download](https://s3.amazonaws.com/fast-ai-imageclas/imagewang-320.tgz); 
- [160 px download](https://s3.amazonaws.com/fast-ai-imageclas/imagewang-160.tgz). 

## Why Imagenette?

I (Jeremy Howard, that is) mainly made Imagenette because I wanted a small vision dataset I could use to quickly see if my algorithm ideas might have a chance of working. They normally don't, but testing them on Imagenet takes a really long time for me to find that out, especially because I'm interested in algorithms that perform particularly well at the *end* of training.

But I think this can be a useful dataset for others as well.

## Usage

If you are already using the [fastai library](https://docs.fast.ai), you can _download and access_ these quickly with commands like:
```python
path = untar_data(URLs.IMAGENETTE_160)
```
where `path` now stores the destination to ImageNette-160.  

### For researchers

- Try to create a classifier that's as accurate as possible under various constraints (we'll keep leaderboards below, submit your PR with a link to your repo or gist!), such as:
  - Within a certain number of epochs: 5, 20, 40, 160
  - Within a certain budget on AWS or GCP (use spot or interruptible instances to save money): $0.05, $0.10, $0.25, $0.50, $1.00, $2.00
- Experiment with other low resource problems like transfer learning from small datasets, using semi-supervised learning to help classify small datasets, etc
- Test the impact of using different sized images, either separately, or together as part of training (i.e. progressive resizing)
- Compare your algorithm on easy vs hard small datasets, which are otherwise very similar (Imagenette vs Imagewoof)
- Ensure that you start from random weights - not from pretrained weights.

### For students

- Practice your modeling skills on a dataset that's very similar to Imagenet, but much less expensive to deal with
- Do send me a PR with your other applications for this dataset!

## Tips

- Because there are only 10 categories, the usual "top 5 accuracy" isn't so interesting. So you should generally report top 1 accuracy when using Imagenette
- The best approaches to 5 epoch training often don't scale well to more epochs
- Data augmentation like mixup tends to only help for 80+ epochs

## Leaderboard

Generally you'll see +/- 1% differences from run to run since it's quite a small validation set. So please only send in contributions that are higher than the reported accuracy >80% of the time. Here's the rules:

- No inference time tricks, e.g. no: TTA, validation size > train size
- Must start with random weights
- Must be one of the size/#epoch combinations listed in the table
- If you have the resources to do so, try to get an average of 5 runs, to get a stable comparison. Use the "# Runs" column to include this (note that `train_imagenette.py` provides a `--runs` flag to make this easy)
- In the URL column include a link to a notebook, blog post, gist, or similar which explains what you did to get your result, and includes the code you used (or a link to it), including the exact commit, so that others can reproduce your result.

### Imagenette Leaderboard

| Size (px) | Epochs | URL | Accuracy | # Runs |
|--|--|--|--|--|
|128|5|[fastai2 train_imagenette.py 2020-10 (mini net)](https://github.com/pete88b/data-science/blob/master/fastai-things/train-imagenette-mininet.ipynb)|85.77%|5, mean|
|128|20|[fastai2 train_imagenette.py 2020-01 + MaxBlurPool](https://github.com/ducha-aiki/imagewoofv2-fastv2-maxpoolblur/blob/master/fastai2-imagenette-train-maxblurpool.ipynb)|91.57%|5, mean|
|128|80|[fastai2 train_imagenette.py 2020-01](https://github.com/fastai/imagenette/blob/master/2020-01-train.md)|93.55%|1|
|128|200|[fastai2 train_imagenette.py 2020-01](https://github.com/fastai/imagenette/blob/master/2020-01-train.md)|94.24%|1|
|192|5|[fastai2 train_imagenette.py 2020-01 + MaxBlurPool](https://github.com/ducha-aiki/imagewoofv2-fastv2-maxpoolblur/blob/master/fastai2-imagenette-train-maxblurpool.ipynb)|86.76%|5, mean|
|192|20|[fastai2 train_imagenette.py 2020-01 + MaxBlurPool](https://github.com/ducha-aiki/imagewoofv2-fastv2-maxpoolblur/blob/master/fastai2-imagenette-train-maxblurpool.ipynb)|92.50%|5, mean|
|192|80|[fastai2 train_imagenette.py 2020-01](https://github.com/fastai/imagenette/blob/master/2020-01-train.md)|94.50%|1|
|192|200|[fastai2 train_imagenette.py 2020-01](https://github.com/fastai/imagenette/blob/master/2020-01-train.md)|95.03%|1|
|256|5|[fastai2 train_imagenette.py 2020-01 + MaxBlurPool](https://github.com/ducha-aiki/imagewoofv2-fastv2-maxpoolblur/blob/master/fastai2-imagenette-train-maxblurpool.ipynb)|86.85%|5, mean|
|256|20|[fastai2 train_imagenette.py 2020-01 + MaxBlurPool](https://github.com/ducha-aiki/imagewoofv2-fastv2-maxpoolblur/blob/master/fastai2-imagenette-train-maxblurpool.ipynb)|93.53%|5,  mean|
|256|80|[fastai2 train_imagenette.py 2020-01](https://github.com/fastai/imagenette/blob/master/2020-01-train.md)|94.90%|1|
|256|200|[fastai2 train_imagenette.py 2020-01](https://github.com/fastai/imagenette/blob/master/2020-01-train.md)|95.11%|1|

### Imagenette w/Label Noise = 5%

Size | Epochs | URL | Accuracy | Runs
-- | -- | -- | -- | --
128 | 5 | [baseline](https://github.com/tmabraham/noisy_imagenette/blob/main/baseline/line-01-18-2021.md) | 0.834395 | 1
128 | 20 | [baseline](https://github.com/tmabraham/noisy_imagenette/blob/main/baseline/line-01-18-2021.md) |0.895287 | 1
128 | 80 | [baseline](https://github.com/tmabraham/noisy_imagenette/blob/main/baseline/line-01-18-2021.md) |0.892994 | 1
128 | 200 | [baseline](https://github.com/tmabraham/noisy_imagenette/blob/main/baseline/line-01-18-2021.md) |0.900382 | 1
192 | 5 | [baseline](https://github.com/tmabraham/noisy_imagenette/blob/main/baseline/line-01-18-2021.md) |0.841274 | 1
192 | 20 | [baseline](https://github.com/tmabraham/noisy_imagenette/blob/main/baseline/line-01-18-2021.md) |0.906497 | 1
192 | 80 | [baseline](https://github.com/tmabraham/noisy_imagenette/blob/main/baseline/line-01-18-2021.md) |0.910064 | 1
192 | 200 | [baseline](https://github.com/tmabraham/noisy_imagenette/blob/main/baseline/line-01-18-2021.md) |0.910828 | 1
256 | 5 | [baseline](https://github.com/tmabraham/noisy_imagenette/blob/main/baseline/line-01-18-2021.md) |0.846115 | 1
256 | 20 | [baseline](https://github.com/tmabraham/noisy_imagenette/blob/main/baseline/line-01-18-2021.md) |0.913885 | 1
256 | 80 | [baseline](https://github.com/tmabraham/noisy_imagenette/blob/main/baseline/line-01-18-2021.md) |0.915924 | 1
256 | 200 |[baseline](https://github.com/tmabraham/noisy_imagenette/blob/main/baseline/baseline-01-18-2021.md) | 0.920255 | 1

### Imagenette w/Label Noise = 50%

Size | Epochs | URL | Accuracy | Runs
-- | -- | -- | -- | --
128 | 5 | [baseline](https://github.com/tmabraham/noisy_imagenette/blob/main/baseline/baseline-01-18-2021.md) | 0.665987 | 1
128 | 20 | [baseline](https://github.com/tmabraham/noisy_imagenette/blob/main/baseline/baseline-01-18-2021.md) | 0.793631 | 1
128 | 80 | [baseline](https://github.com/tmabraham/noisy_imagenette/blob/main/baseline/baseline-01-18-2021.md) | 0.508025 | 1
128 | 200 | [baseline](https://github.com/tmabraham/noisy_imagenette/blob/main/baseline/baseline-01-18-2021.md) | 0.521783 | 1
192 | 5 | [baseline](https://github.com/tmabraham/noisy_imagenette/blob/main/baseline/baseline-01-18-2021.md) | 0.675414 | 1
192 | 20 | [baseline](https://github.com/tmabraham/noisy_imagenette/blob/main/baseline/baseline-01-18-2021.md) | 0.793376 | 1
192 | 80 | [baseline](https://github.com/tmabraham/noisy_imagenette/blob/main/baseline/baseline-01-18-2021.md) | 0.525096 | 1
192 | 200 | [baseline](https://github.com/tmabraham/noisy_imagenette/blob/main/baseline/baseline-01-18-2021.md) | 0.53707 | 1
256 | 5 | [baseline](https://github.com/tmabraham/noisy_imagenette/blob/main/baseline/baseline-01-18-2021.md) | 0.650446 | 1
256 | 20 | [baseline](https://github.com/tmabraham/noisy_imagenette/blob/main/baseline/baseline-01-18-2021.md) | 0.792102 | 1
256 | 80 | [baseline](https://github.com/tmabraham/noisy_imagenette/blob/main/baseline/baseline-01-18-2021.md) | 0.539618 | 1
256 | 200 | [baseline](https://github.com/tmabraham/noisy_imagenette/blob/main/baseline/baseline-01-18-2021.md) | 0.55414 | 1

----

### Imagewoof Leaderboard

| Size (px) | Epochs | URL | Accuracy | # Runs |
|--|--|--|--|--|
|128|5|[depthwise(x6)](https://github.com/liuyao12/imagenette_experiments/blob/master/ResNet_separable.ipynb)|76.61%|5, mean|
|128|20|[depthwise(x4)](https://github.com/liuyao12/imagenette_experiments/blob/master/ResNet_separable.ipynb)|86.27%|5, mean|
|128|80|[depthwise(x4)](https://github.com/liuyao12/imagenette_experiments/blob/master/ResNet_separable.ipynb)|87.83%|1|
|128|200|[fastai2 train_imagenette.py 2020-01](https://github.com/fastai/imagenette/blob/master/2020-01-train.md)|87.20%|1|
|192|5|[depthwise(x4)](https://github.com/liuyao12/imagenette_experiments/blob/master/ResNet_separable.ipynb)|81.15%|5, mean|
|192|20|[depthwise(x4)](https://github.com/liuyao12/imagenette_experiments/blob/master/ResNet_separable.ipynb)|88.37%|5, mean|
|192|80|[depthwise(x2)](https://github.com/liuyao12/imagenette_experiments/blob/master/ResNet_separable.ipynb)|90.30%|1|
|192|200|[fastai2 train_imagenette.py 2020-01](https://github.com/fastai/imagenette/blob/master/2020-01-train.md)|89.54%|1|
|256|5|[Resnet Trick + Mish + Sa + MaxBlurPool](https://github.com/ayasyrev/imagenette_experiments/blob/master/Woof_MaxBlurPool_ResnetTrick_s256bs32.ipynb)|78,84%|5, mean|
|256|20|[Resnet Trick + Mish + Sa + MaxBlurPool](https://github.com/ayasyrev/imagenette_experiments/blob/master/Woof_MaxBlurPool_ResnetTrick_s256bs32.ipynb)|88,58%|5, mean|
|256|80|[fastai2 train_imagenette.py 2020-01](https://github.com/fastai/imagenette/blob/master/2020-01-train.md)|90.48%|1|
|256|200|[fastai2 train_imagenette.py 2020-01](https://github.com/fastai/imagenette/blob/master/2020-01-train.md)|90.38%|1|

----

### Image网 Leaderboard

| Size (px) | Epochs | URL | Accuracy | # Runs |
|--|--|--|--|--|
|128|5|[SwAV](https://github.com/KeremTurgutlu/self_supervised/blob/682c1e5367c2779f3ed0f8a0dc15a5abd27d5a0f/nbs/examples/swav_iwang_128.ipynb)|63.42%| 5,mean|
|128|20|[SwAV](https://github.com/KeremTurgutlu/self_supervised/blob/682c1e5367c2779f3ed0f8a0dc15a5abd27d5a0f/nbs/examples/swav_iwang_128.ipynb)|67.11%|3,mean|
|128|80|[SwAV](https://github.com/KeremTurgutlu/self_supervised/blob/682c1e5367c2779f3ed0f8a0dc15a5abd27d5a0f/nbs/examples/swav_iwang_128.ipynb)|66.78%|1|
|128|200|[SwAV](https://github.com/KeremTurgutlu/self_supervised/blob/682c1e5367c2779f3ed0f8a0dc15a5abd27d5a0f/nbs/examples/swav_iwang_128.ipynb)|64.87%|1|
|192|5|[SwAV](https://github.com/KeremTurgutlu/self_supervised/blob/eeab0ae53c47a5c9c66759d9350a66963606cacb/nbs/examples/swav_iwang_192.ipynb)|72.33%|5,mean|
|192|20|[SwAV](https://github.com/KeremTurgutlu/self_supervised/blob/eeab0ae53c47a5c9c66759d9350a66963606cacb/nbs/examples/swav_iwang_192.ipynb)|74.93%|3,mean|
|192|80|[SwAV](https://github.com/KeremTurgutlu/self_supervised/blob/eeab0ae53c47a5c9c66759d9350a66963606cacb/nbs/examples/swav_iwang_192.ipynb)|73.07%|1|
|192|200|[SwAV](https://github.com/KeremTurgutlu/self_supervised/blob/eeab0ae53c47a5c9c66759d9350a66963606cacb/nbs/examples/swav_iwang_192.ipynb)|71.77%|1|
|256|5|[SwAV](https://github.com/KeremTurgutlu/self_supervised/blob/159a11ba969beebeac41f71453615eb4bc9f9efc/nbs/examples/swav_iwang_224.ipynb)|73.17%|5,mean|
|256|20|[SwAV](https://github.com/KeremTurgutlu/self_supervised/blob/159a11ba969beebeac41f71453615eb4bc9f9efc/nbs/examples/swav_iwang_224.ipynb)|76.49%|3,mean|
|256|80|[SwAV](https://github.com/KeremTurgutlu/self_supervised/blob/159a11ba969beebeac41f71453615eb4bc9f9efc/nbs/examples/swav_iwang_224.ipynb)|75.46%|1|
|256|200|[SwAV](https://github.com/KeremTurgutlu/self_supervised/blob/159a11ba969beebeac41f71453615eb4bc9f9efc/nbs/examples/swav_iwang_224.ipynb)|73.98%|1|
