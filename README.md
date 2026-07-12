# Comparing Text Classification Models on News Topics

## What this project does
This project compares four different ways to classify news headlines into
topics. The models go from very simple to more complex:
1. Bag-of-Words + Logistic Regression
2. A small Feedforward Neural Network
3. An LSTM
4. DistilBERT (a pretrained model)

**My question:** Does a more complex model actually do better? And if it
does, is the extra time and effort worth it?

## The data
- I used the AG News dataset, downloaded through the HuggingFace `datasets`
  library (`load_dataset("ag_news")`).
- It's free to use for research.
- There are 4 topics: World, Sports, Business, and Sci/Tech.
- I used a small part of the full dataset to keep things fast:
  4,000 examples for training, 500 for validation, and 500 for testing.
- I used a fixed random seed (42) so the same examples get picked every time.

## How to set it up

You need Python 3.9 or newer. The exact package versions I used are listed
in `requirements.txt`.

```bash
python3 -m venv venv
source venv/bin/activate      # On Windows, use: venv\Scripts\activate
pip install -r requirements.txt
```

## How to run it

1. Turn on the virtual environment (see above).
2. Start Jupyter:
```bash
   jupyter notebook
```
3. Open `notebook.ipynb`.
4. Run all the cells from top to bottom (Kernel → Restart & Run All).

The notebook will automatically:
- Download the AG News dataset (no manual download needed)
- Download the DistilBERT model (about 250MB, only happens once)
- Train and test all four models
- Save a picture of the confusion matrices to `data/confusion_matrices.png`
- Print the final results and some examples the models got wrong

## Why the results are reproducible
I used the same random seed (42) everywhere — for Python, NumPy, and
PyTorch. All the settings I used for each model (like learning rate and
number of epochs) are written directly in the notebook, in the cell where
each model is built.

## My results, briefly
Full results, confusion matrices, and error analysis are in `notebook.ipynb`
and in my report. The final accuracy on the test set ranged from 81.2%
(LSTM) to 89.8% (Bag-of-Words baseline).

## What's in this folder
- `notebook.ipynb` — all my code: loading data, training models, testing
  them, and looking at errors
- `requirements.txt` — the exact package versions I used
- `notes.md` — my working notes as I went along
- `data/confusion_matrices.png` — a picture showing what each model got
  right and wrong
- `README.md` — this file
