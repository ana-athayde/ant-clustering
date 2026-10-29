# Ant Clustering

This repository explores **ant-based clustering**, a bio-inspired approach in which simple agents move through a grid and organize items using only local information. The project is organized into two parts: clustering identical items and clustering numerical data points.

## How It Works

In both simulations, ants move randomly across a grid with wraparound edges. An ant evaluates nearby items and probabilistically picks up or drops an item based on the local density of similar items. Repeating these local interactions can form visible groups without a central controller.

For numerical data, similarity is based on Euclidean distance between each point's two features. Data is normalized before it is placed randomly on the grid. The CSV class labels are retained to color points in visualizations; they are not used to make pick-up or drop decisions.

## Repository Contents

| Path | Description |
| --- | --- |
| [`Parte 01/FormigasParte01.ipynb`](Parte%2001/FormigasParte01.ipynb) | Simulates clustering identical items on a grid. |
| [`Parte 02/FormigasParte02.ipynb`](Parte%2002/FormigasParte02.ipynb) | Applies ant clustering to the general-purpose `Parte 02/Base.csv` dataset. |
| [`FormigasParte02_Base4.ipynb`](FormigasParte02_Base4.ipynb) | Runs the numerical-data simulation on `Base4.csv` (four labeled groups). |
| [`FormigasParte02_Base15.ipynb`](FormigasParte02_Base15.ipynb) | Runs the numerical-data simulation on `Base15.csv` (15 labeled groups). |
| `Base.csv`, `Base4.csv`, `Base15.csv` | Input datasets containing two numeric features and a class label. |
| [`requirements.txt`](requirements.txt) | Python package dependencies. |

The notebooks in the repository root expect their CSV files to be available in the current working directory. When running them, start Jupyter from the repository root. The notebooks under `Parte 01/` and `Parte 02/` use files relative to their working directory; run those notebooks with their respective part directory as the working directory, or adjust the data path in the notebook.

## Setup

Python 3 and Jupyter Notebook are required. From the repository root, install the dependencies and start Jupyter:

```bash
python -m pip install -r requirements.txt
jupyter notebook
```

Open the notebook you want to run and execute its cells in order. The simulations use Python, NumPy, pandas, Matplotlib, and ImageIO; `ipykernel` and `notebook` provide the notebook environment.

## Simulations

### Part 1: Identical Items

[`Parte 01/FormigasParte01.ipynb`](Parte%2001/FormigasParte01.ipynb) creates a 50 × 50 grid with 600 identical items and 15 ants. It runs for 100,000 iterations and saves visualizations of the initial and final grid as `ambiente_Estado Inicial.png` and `ambiente_Estado Final.png` (the exact filenames are formed from the title in the notebook).

### Part 2: Numerical Data

The numerical-data notebooks normalize two-dimensional points, distribute them across a 64 × 64 grid, and record the simulation as an animated GIF alongside initial and final images.

| Notebook | Input | Ants | Iterations | Similarity parameters (`k1`, `k2`, `alpha`) |
| --- | --- | ---: | ---: | --- |
| [`Parte 02/FormigasParte02.ipynb`](Parte%2002/FormigasParte02.ipynb) | `Parte 02/Base.csv` | 100 | 1,000,000 | 0.1, 0.3, 0.25 |
| [`FormigasParte02_Base4.ipynb`](FormigasParte02_Base4.ipynb) | `Base4.csv` | 100 | 1,000,000 | 0.1, 0.3, 0.25 |
| [`FormigasParte02_Base15.ipynb`](FormigasParte02_Base15.ipynb) | `Base15.csv` | 15 | 3,000,000 | 0.9, 0.05, 0.11 |

The data notebooks write files such as `estado_inicial.png`, `estado_final.png`, and `ant_clustering.gif` to the current working directory. The 15-group notebook uses suffixed filenames to distinguish its outputs. The iteration counts can make runs take a while; change the simulation configuration cell to experiment with fewer iterations, ants, or different parameter values.

## Dataset Format

Each row represents one point with two feature values and a class label. `Base15.csv` is tab-separated, `Base4.csv` is comma-separated and uses quoted decimal commas in the feature values, and `Parte 02/Base.csv` is read as a comma-separated file. The corresponding notebook contains the loader for that dataset's format.

The labels are used to color points in the grid image, so visualizations show the original class identity. The simulation's similarity calculation uses only the feature values; it does not use class labels to cluster points.

## Notes

- The simulations use random initialization and random ant movement, so results can vary between runs.
- The notebooks primarily demonstrate clustering visually; they do not calculate clustering evaluation metrics.
- The suggested parameter values are starting points for experimentation, not guaranteed optimal settings.
