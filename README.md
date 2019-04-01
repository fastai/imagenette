# Imagenette

> 🎶 *Imagenette, gentille imagenette,*
>
> *Imagenette, je te plumerai.* 🎶
>
> (Imagenette theme song thanks to [Samuel Finlayson](https://twitter.com/IAmSamFin/status/1103737947004854272))

This is the home of Imagenette: a subset of 10 easily classified classes from Imagenet (tench, English springer, cassette player, chain saw, church, French horn, garbage truck, gas pump, golf ball, parachute).

'Imagenette' is pronounced just like 'Imagenet', except with a corny inauthentic French accent. If you've seen Peter Sellars in The Pink Panther, then think something like that. It's important to ham up the accent as much as possible, otherwise people might not be sure whether you're refering to "Imagenette" or "Imagenet". (*Note to native French speakers: to avoid confusion, be sure to use a corny inauthentic American accent when saying "Imagenet". Think something like the [philosophy restaurant skit](https://www.youtube.com/watch?v=oa0bCzwSNA0) from Monty Python's The Meaning of Life.*)

Here are the datasets: [Full size](https://s3.amazonaws.com/fast-ai-imageclas/imagenette.tgz); [320 px](https://s3.amazonaws.com/fast-ai-imageclas/imagenette-320.tgz); [160 px](https://s3.amazonaws.com/fast-ai-imageclas/imagenette-160.tgz). The '320 px' and '160 px' versions have their shortest size resized to that size, with their aspect ratio maintained.

Too easy for you? In that case, you might want to try **Imagewoof**, a subset of 10 classes from Imagenet that aren't so easy to classify, since they're all dog breeds. Here they are: [Full size](https://s3.amazonaws.com/fast-ai-imageclas/imagewoof.tgz); [320 px](https://s3.amazonaws.com/fast-ai-imageclas/imagewoof-320.tgz); [160 px](https://s3.amazonaws.com/fast-ai-imageclas/imagewoof-160.tgz). The breeds are: Australian terrier, Border terrier, Samoyed, Beagle, Shih-Tzu, English foxhound, Rhodesian ridgeback, Dingo, Golden retriever, Old English sheepdog. (No we will not enter in to any discussion in to whether a dingo is in fact a dog. Any suggestions to the contrary are un-Australian. Thank you for your cooperation.)

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
- ...more to come...

## Leaderboard

Generally you'll see +/- 1% differences from run to run since it's quite a small validation set. So please only send in contributions that are higher than the reported accuracy >80% of the time.

### Imagenette

### 160px: 5 epoch max

| Accuracy | URL | Params | Notes |
|--|--|--|--|
| 81.6 | [examples/train_imagenette.py](https://github.com/fastai/fastai/blob/master/examples/train_imagenette.py) | `--epochs 5 --bs 32 --lr 4e-3 --mixup 0` | 2 GPUs |

### 192px: 5 epoch max

| Accuracy | URL | Params | Notes |
|--|--|--|--|
| NA | NA | NA | NA |

### 256px: 5 epoch max

| Accuracy | URL | Params | Notes |
|--|--|--|--|
| NA | NA | NA | NA |

----

### 128px: 20 epoch max

| Accuracy | URL | Params | Notes |
|--|--|--|--|
| 92.0 | [examples/train_imagenette.py](https://github.com/fastai/fastai/blob/master/examples/train_imagenette.py) | `--epochs 20 --bs 128 --lr 3e-3 --mixup 0` | 2 GPUs |

### 192px: 20 epoch max

| Accuracy | URL | Params | Notes |
|--|--|--|--|
| NA | NA | NA | NA |

### 256px: 20 epoch max

| Accuracy | URL | Params | Notes |
|--|--|--|--|
| NA | NA | NA | NA |

----

### 128px: 40 epoch max

| Accuracy | URL | Params | Notes |
|--|--|--|--|
| 91.8 | [examples/train_imagenette.py](https://github.com/fastai/fastai/blob/master/examples/train_imagenette.py) | `--epochs 40 --bs 128 --lr 2e-3 --mixup 0` | 2 GPUs |

### 192px: 40 epoch max

| Accuracy | URL | Params | Notes |
|--|--|--|--|
| NA | NA | NA | NA |

### 256px: 40 epoch max

| Accuracy | URL | Params | Notes |
|--|--|--|--|
| NA | NA | NA | NA |

----

### Imagewoof

### 128px: 5 epoch max

| Accuracy | URL | Params | Notes |
|--|--|--|--|
| 51.6 | [examples/train_imagenette.py](https://github.com/fastai/fastai/blob/master/examples/train_imagenette.py) | `--epochs 5 --bs 32 --lr 1e-3 --mixup 0 --woof 1` | 2 GPUs |

### 192px: 5 epoch max

| Accuracy | URL | Params | Notes |
|--|--|--|--|
| NA | NA | NA |

### 256px: 5 epoch max

| Accuracy | URL | Params | Notes |
|--|--|--|--|
| NA | NA | NA | NA |

----

### 128px: 20 epoch max

| Accuracy | URL | Params | Notes |
|--|--|--|--|
| 75.4 | [examples/train_imagenette.py](https://github.com/fastai/fastai/blob/master/examples/train_imagenette.py) | `--epochs 20 --bs 128 --lr 2e-3 --woof 1 --mixup 0` |

### 192px: 20 epoch max

| Accuracy | URL | Params | Notes |
|--|--|--|--|
| NA | NA | NA | NA |

### 256px: 20 epoch max

| Accuracy | URL | Params | Notes |
|--|--|--|--|
| NA | NA | NA | NA |

----

### 128px: 40 epoch max

| Accuracy | URL | Params | Notes |
|--|--|--|--|
| 84.2 | [examples/train_imagenette.py](https://github.com/fastai/fastai/blob/master/examples/train_imagenette.py) | `--epochs 40 --bs 128 --lr 3e-3 --woof 1` | 2 GPUs |

### 192px: 40 epoch max

| Accuracy | URL | Params | Notes |
|--|--|--|--|
| NA | NA | NA | NA |

### 256px: 40 epoch max

| Accuracy | URL | Params | Notes |
|--|--|--|--|
| NA | NA | NA | NA |
