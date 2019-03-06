# Imagenette

This is the home of Imagenette: a subset of 10 easily classified classes from Imagenet (tench, English springer, cassette player, chain saw, church, French horn, garbage truck, gas pump, golf ball, parachute).

'Imagenette' is pronounced just like 'Imagenet', except with a corny inauthentic French accent. If you've seen Peter Sellars in The Pink Panther, then think something like that. It's important to ham up the accent as much as possible, otherwise people might not be sure whether you're refering to "Imagenette" or "Imagenet". (*Note to native French speakers: to avoid confusion, be sure to use a corny inauthentic American accent when saying "Imagenet". Think something like the [philosophy restaurant skit](https://www.youtube.com/watch?v=oa0bCzwSNA0) from Monty Python's The Meaning of Life.*)

Here are the datasets: [Full size](https://s3.amazonaws.com/fast-ai-imageclas/imagenette.tgz); [320 px](https://s3.amazonaws.com/fast-ai-imageclas/imagenette-320.tgz); [160 px](https://s3.amazonaws.com/fast-ai-imageclas/imagenette-160.tgz). The '320 px' and '160 px' versions have their shortest size resized to that size, with their aspect ratio maintained.

## Why Imagenette?

I (Jeremy Howard, that is) mainly made Imagenette because I wanted a small vision dataset I could use to quickly see if my algorithm ideas might have a chance of working. They normally don't, but testing them on Imagenet takes a really long time for me to find that out, especially because I'm interested in algorithms that perform particularly well at the *end* of training.

But I think this can be a useful dataset for others as well.

### For researchers

- Try to create a classifier that's as accurate as possible under various constraints (we'll keep leaderboards below, submit your PR with a link to your repo or gist!), such as:
  - Within a certain number of epochs: 5, 10, 30, 60
  - Within a certain budget on AWS or GCP (use spot or interruptible instances to save money): $0.05, $0.10, $0.25, $0.50, $1.00, $2.00
- Experiment with other low resource problems like transfer learning from small datasets, using semi-supervised learning to help classify small datasets, etc
- Test the impact of using different sized images, either separately, or together as part of training (i.e. progressive resizing)

### For students

- Practice your modeling skills on a dataset that's very similar to Imagenet, but much less expensive to deal with

...send me a PR with your other applications for this dataset!...

## Tips

- Because there are only 10 categories, the usual "top 5 accuracy" isn't so interesting. So you should generally report top 1 accuracy when using Imagenette
- ...more to come...

## Leaderboard

### 30 epoch max

- See examples/train_imagenette.py in the fastai repo for an example that you should be able to get close to 90% top 1! (Jeremy just hit that mark; he'll share his script soon.)
