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

Generally you'll see +/- 1% differences from run to run since it's quite a small validation set. So please only send in contributions that are higher than the reported accuracy >80% of the time. Here's the rules:

- No inference time tricks, e.g. no: TTA, validation size > train size
- Must start with random weights
- Must be one of the size/#epoch combinations listed in the table

### Imagenette

| Size (px) | Epochs | Accuracy | URL | Params | GPUs |
|--|--|--|--|--|--|
| 128 | 5 | 84.6 | [link](https://github.com/fastai/fastai/blob/master/examples/train_imagenette.py) | `--epochs 5 --bs 64 --lr 3e-3 --mixup 0` | 4 |
| 192 | 5 | 86.6 | [link](https://github.com/fastai/fastai/blob/master/examples/train_imagenette.py) | `--epochs 5 --bs 64 --lr 1e-2 --mixup 0 --woof 0 --size 192` | 3 |
| 256 | 5 | 84.2 | [link](https://github.com/fastai/fastai/blob/master/examples/train_imagenette.py) | `--epochs 5 --bs 64 --lr 1e-2 --mixup 0 --woof 0 --size 256` | 3 |
| 128 | 20 | 92.0 | [link](https://github.com/fastai/fastai/blob/master/examples/train_imagenette.py) | `--epochs 20 --bs 128 --lr 3e-3 --mixup 0` | 2 |
| 192 | 20 | 93.0 | [link](https://github.com/fastai/fastai/blob/master/examples/train_imagenette.py) | `--epochs 20 --bs 64 --lr 1e-2 --mixup 0 --woof 0 --size 192` | 3 |
| 256 | 20 | 93.0 | [link](https://github.com/fastai/fastai/blob/master/examples/train_imagenette.py) | `--epochs 20 --bs 64 --lr 1e-2 --mixup 0 --woof 0 --size 256` | 3 |
| 128 | 80 | 94.2 | [link](https://github.com/fastai/fastai/blob/master/examples/train_imagenette.py) | `--epochs 80 --bs 64 --lr 1e-2 --mixup 0.2 --woof 0 --size 128` | 3 |
| 192 | 80 | 95.2 | [link](https://github.com/fastai/fastai/blob/master/examples/train_imagenette.py) | `--epochs 80 --bs 64 --lr 1e-2 --mixup 0.2 --woof 0 --size 192` | 3 |
| 256 | 80 | 95.8 | [link](https://github.com/fastai/fastai/blob/master/examples/train_imagenette.py) | `--epochs 80 --bs 64 --lr 1e-2 --mixup 0.2 --woof 0 --size 256` | 3 |
| 128 | 400 | 94.6 | [link](https://github.com/fastai/fastai/blob/master/examples/train_imagenette.py) | `--epochs 400 --bs 64 --lr 1e-2 --mixup 0.2 --woof 0 --size 128` | 3 |
| 192 | 400 | 96.4 | [link](https://github.com/fastai/fastai/blob/master/examples/train_imagenette.py) | `--epochs 400 --bs 64 --lr 1e-2 --mixup 0.2 --woof 0 --size 192` | 3 |
| 256 | 400 | NA | NA | NA | NA |

----

### Imagewoof

| Size (px) | Epochs | Accuracy | URL | Params | GPUs |
|--|--|--|--|--|--|
| 128 | 5 | 51.6 | [link](https://github.com/fastai/fastai/blob/master/examples/train_imagenette.py) | `--epochs 5 --bs 32 --lr 1e-3 --mixup 0 --woof 1` | 2 |
| 192 | 5 | NA | NA | N4 | NA |
| 256 | 5 | NA | NA | N4 | NA |
| 128 | 20 | 75.4 | [link](https://github.com/fastai/fastai/blob/master/examples/train_imagenette.py) | `--epochs 20 --bs 128 --lr 2e-3 --woof 1 --mixup 0` | 2 |
| 192 | 20 | NA | NA | NA | NA |
| 256 | 20 | NA | NA | NA | NA |
| 128 | 80 | 86.2 | [link](https://github.com/fastai/fastai/blob/master/examples/train_imagenette.py) | `--epochs 80 --bs 64 --lr 1e-2 --mixup 0.2 --arch xresnet50 --woof 1` | 4 |
| 192 | 80 | NA | NA | NA | NA |
| 256 | 80 | NA | NA | NA | NA |
| 128 | 400 | 87.0 | [link](https://github.com/fastai/fastai/blob/master/examples/train_imagenette.py) | `--epochs 400 --bs 64 --lr 1e-2 --arch xresnet50 --woof 1` | 4 |
| 192 | 400 | 89.4 | [link](https://github.com/fastai/fastai/blob/master/examples/train_imagenette.py) | `--epochs 400 --bs 64 --lr 1e-2 --mixup 0.2 --woof 1 --size 192` | 4 |
| 256 | 400 | 90.2 | [link](https://github.com/fastai/fastai/blob/master/examples/train_imagenette.py) | `--epochs 400 --bs 64 --lr 1e-2 --mixup 0.2 --woof 1 --size 256` | 4 |
