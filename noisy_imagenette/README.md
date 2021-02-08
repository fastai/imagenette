# Noisy Imagenette

This folder includes more information about the noisy version of Imagenette/Imagewoof, which is available with the current Imagenette/Imagewoof dataset as CSV files. Note that the Imagenette datasets with 5% and 50% noise are the main versions of the noisy dataset, with the leaderboards maintained [here](README.md).

This folder contains the following files:
- `generate_labels.ipynb`: The Jupyter Notebook used to generate the noisy labels ([Noisy Imagenette CSV](noisy_imagenette.csv) and [Noisy Imagewoof CSV](noisy_imagewoof.csv))
- `extended_lb.csv`: This includes accuracy scores for all image sizes (128, 192, 256), number of epochs (5, 20, 80, 200), with an expanded set of noise levels (1%, 5%, 25%, 50%) on both Imagenette and Imagewoof, resulting in 96 scores. The CSV includes scores from [this baseline](https://github.com/tmabraham/noisy_imagenette/tree/main/baseline).
