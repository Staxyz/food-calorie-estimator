# Food Recognition & Calorie Estimation

Classify food in a photo with a pretrained image model (via `timm`) and estimate calories by looking up the predicted dish in a nutrition table.

## Folder structure

```
data/
  nutrition/      Small CSV files with calories/macros per dish (committed to git)
  raw/            Original downloaded datasets (ignored by git)
  processed/      Resized images, splits, cached features (ignored by git)
notebooks/        Exploration and training notebooks (run in Colab)
src/              Reusable Python code: datasets, models, training, inference
app/              Gradio demo app
reports/figures/  Plots and figures for reports (committed)
models/           Trained weights and checkpoints (ignored by git)
```

Large data and model files are never committed — see `.gitignore`. Empty folders are kept in git with `.gitkeep` files.

## Workflow

1. **Develop locally with Claude Code** — write and edit code in `src/`, `app/` and `notebooks/`.
2. **Push to GitHub**
   ```bash
   git add .
   git commit -m "Describe your change"
   git push
   ```
3. **Train in Colab** — open a notebook, enable a GPU runtime, then:
   ```python
   !git clone https://github.com/<your-user>/<your-repo>.git
   %cd <your-repo>
   !pip install -q -r requirements.txt
   ```
   Download datasets into `data/raw/` and save checkpoints to `models/` (or to Google Drive so they survive the session). After code changes, run `!git pull` to get the latest version.

## Requirements

`torch` and `torchvision` are deliberately not in `requirements.txt` because Colab already has them. For local use, install them first from [pytorch.org](https://pytorch.org/get-started/locally/), then:

```bash
pip install -r requirements.txt
```

## Running the app

```bash
python app/app.py
```
