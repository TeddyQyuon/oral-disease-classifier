# Oral Disease Image Classifier v2 (IT2226)

A Colab notebook that trains an image classifier for six oral conditions: **Calculus, Hypodontia, Mouth ulcer, Normal, caries, tooth discoloration**. It upgrades the original `AIDL_proj.ipynb` by fixing data leakage, adding a proper train/validation/test split, comparing several models and producing a model file ready for an app.

> Student project. The model is a screening aid only and is not a medical diagnosis.

## Files

| File | Purpose |
|---|---|
| `AIDL_proj_v2.ipynb` | The full pipeline: data download, EDA, cleaning, near-duplicate grouping, split, training experiments, evaluation, Grad-CAM, model export |
| `README.md` | This guide |
| `IT2226_Study_Guide.md` | Study guide covering the six IT2226 course documents |

The dataset is not stored in this repo. The notebook downloads it from Kaggle: [Oral Image Dataset](https://www.kaggle.com/datasets/jhirshaikh/oral-image-dataset) (licence CC0-1.0, about 430 MB).

**To download this repo:** on the repo page click `Code > Download ZIP`, or run `git clone https://github.com/TeddyQyuon/oral-disease-classifier.git`.

## How to train on Google Colab (T4 GPU)

### 1. Open the notebook in Colab

Pick one of these:

- **From GitHub:** in Colab, choose `File > Open notebook > GitHub`, tick **Include private repos** (this repo is private, so Colab asks you to authorise GitHub once), search `TeddyQyuon/oral-disease-classifier` and open `AIDL_proj_v2.ipynb`.
- **Upload:** download `AIDL_proj_v2.ipynb` from this repo, then in Colab choose `File > Upload notebook`.

### 2. Select the T4 GPU

`Runtime > Change runtime type > Hardware accelerator: T4 GPU > Save`.

The setup cell (second code cell) prints the device. It should say `cuda | Tesla T4`. If it says `no GPU`, the runtime type was not saved.

### 3. Give the notebook your Kaggle API token

Get a token at [kaggle.com](https://www.kaggle.com) > your profile > **Settings** > **API** > **Create New Token**. This is the same kind of token you used in v1.

Then do **one** of these:

- **Recommended (Colab secret):** click the key icon in Colab's left sidebar, add a secret named `KAGGLE_API_TOKEN`, paste the token as its value and switch on **Notebook access**. The notebook reads it automatically.
- **Paste when asked:** run the notebook and paste the token into the password box that appears in section 2.
- **Legacy `kaggle.json` file:** if your token is a `kaggle.json` file with `username` and `key`, upload it to `~/.kaggle/kaggle.json` in the Colab session before section 2 runs.

The token is never saved inside the notebook.

### 4. Run everything

`Runtime > Run all`. Stay on the page, because Colab may pause idle sessions.

What happens, by notebook section:

| Section | What it does | Check this |
|---|---|---|
| 1 Setup | Installs `grad-cam`, sets config and seed, picks the GPU | Device line shows `Tesla T4` |
| 2 Dataset | Downloads and unzips the Kaggle dataset | Six class folders are listed |
| 3 EDA | Class counts, image sizes, sample grid | Normal images are far larger than the others (possible shortcut) |
| 4 Cleaning | Removes exact duplicates, drops conflicting labels, groups copies of the same photo (embedding similarity plus a keypoint check), handles pre-augmented files | The three image panels in 4.2: linked pairs should be the same photo, rejected pairs mostly different photos |
| 5 Split | Group-aware stratified split, about 72% / 14% / 14% | Prints `Leakage checks passed` and the residual-leakage figures |
| 6 Training | Runs experiments A to D and records each in a table | Experiment table and training curves |
| 7 Test evaluation | Picks the best model on validation, then evaluates the test set once | Per-class recall, confusion matrix, resolution shortcut table |
| 8 Threshold | Picks a confidence threshold for the "uncertain" fallback | Coverage and accuracy at the chosen threshold |
| 9 Grad-CAM | Heatmaps for one correct test image per class | Heat should be on teeth and gums, not background |
| 10 Export | Saves `artifacts/dental_classifier.pt` and `model_card.json` | Prints `Reload check passed.` |
| 11 Try a photo | Upload your own photo for a prediction | |
| 12 Save | Download `artifacts.zip` or copy to Google Drive | |

**Expected time:** roughly 20 to 40 minutes on a T4 in total. Data preparation (sections 2 to 5) takes about 5 minutes, and the rest is the four training experiments. These are estimates. The full notebook was tested on a CPU in smoke-test mode, and sections 1 to 5 were run on the full dataset on a CPU. It has not yet had a full T4 training run.

Expected split on the full dataset (seed 42):

| Class | Train | Val | Test |
|---|---:|---:|---:|
| Calculus | 600 | 101 | 101 |
| Hypodontia | 888 | 168 | 168 |
| Mouth ulcer | 171 | 36 | 36 |
| Normal | 198 | 44 | 42 |
| caries | 135 | 30 | 29 |
| tooth discoloration | 121 | 26 | 26 |
| **Total** | **2,113** | **405** | **402** |

Small differences are possible if Colab's library versions change the image embeddings slightly.

### 5. Keep your results

Colab deletes `/content` when the session ends. Section 12 has two options:

- **Option A** downloads `artifacts.zip` to your computer.
- **Option B** copies `artifacts/` to Google Drive. Set `SAVE_TO_DRIVE = True` in that cell first.

`artifacts/` contains:

| File | Contents |
|---|---|
| `dental_classifier.pt` | Best model weights plus class names, preprocessing settings and confidence threshold |
| `model_card.json` | The same metadata without weights, plus test metrics |
| `experiments.csv` | One row per experiment: architecture, learning rate, best epoch, validation scores, time |
| `training_history.csv` | Per-epoch losses and scores for every experiment |
| `splits.csv` | Which image went to train, validation or test (for checklist Q10) |
| `figures/` | EDA, training curves, confusion matrix, threshold curve, Grad-CAM |
| `checkpoints/` | Best checkpoint of each experiment |

## Changing the training

All settings are in the `CFG` dictionary in the setup cell.

| Setting | Default | Meaning |
|---|---|---|
| `max_epochs` | 25 | Upper limit per experiment |
| `patience` | 6 | Stop after this many epochs without validation macro-F1 improvement |
| `batch_size` | 32 | Lower to 16 if you get `CUDA out of memory` |
| `near_dup_threshold` | 0.86 | Embedding similarity at which two photos are linked directly as copies |
| `geo_min_sim`, `geo_neighbours` | 0.60, 10 | Which less similar pairs get the keypoint check: each photo's 10 nearest photos with similarity of at least 0.60 |
| `orb_features`, `orb_min_inliers` | 500, 15 | Keypoints per image, and how many geometrically consistent matches confirm the same photo |
| `max_eval_group` | 30 | Groups with more photos than this always go to training |
| `use_preaugmented` | False | Keep the 875 `Tooth_Discoloration_0_*` pre-augmented files (training only) |
| `target_selective_acc` | 0.95 | Validation accuracy the confidence threshold aims for |
| `max_side` | 612 | All images shrunk to this longest side before training and inference |

To try more models or hyperparameters, add rows to `EXPERIMENTS` in section 6.3, for example:

```python
dict(name="E_effb0_lr3e-4", arch="efficientnet_b0", lr=3e-4),
dict(name="F_mnv3l_finetune", arch="mobilenet_v3_large", lr=1e-3),
```

Supported `arch` values: `mobilenet_v3_small`, `mobilenet_v3_large`, `efficientnet_b0`, `convnext_tiny`. Other options are `backbone_lr_mult`, `weight_decay`, `warmup_epochs`, `freeze_backbone`, `label_smoothing` and `dropout`. Every run is added to `experiments.csv`, which is your evidence of systematic optimisation for the rubric.

**Quick pipeline check:** to confirm everything runs before a full training, change `SMOKE_TEST = os.environ.get("SMOKE_TEST") == "1"` to `SMOKE_TEST = True`. The notebook then uses 40 images per class and 2 epochs and finishes in a few minutes. Its scores mean nothing. Set it back before real training.

## What changed from v1 and why

| Problem in v1 | Fix in v2 |
|---|---|
| `val_dataset.dataset.transform = ...` also changed the training set's transform, so augmentation never ran | Separate datasets for training and evaluation |
| 553 redundant byte-identical copies; 27 pictures filed under more than one class | Exact duplicates removed; conflicting pictures dropped |
| Pre-augmented and near-duplicate copies could appear in both training and validation, inflating the 92% | Copies of the same photo grouped (embedding similarity plus an ORB keypoint and RANSAC check) and kept in one split |
| No test set, no seed, last epoch saved | Seeded group-aware train/validation/test split, best validation epoch saved, test set used once |
| Accuracy only | Per-class precision/recall/F1, macro-F1, balanced accuracy, ROC-AUC, confusion matrix |
| Single frozen MobileNetV3-Small | Experiment table including a v1-style baseline and fine-tuned larger models |
| Normal photos much larger than other classes | Uniform `max_side` resizing, blur augmentation, results broken down by source resolution |
| Every upload got a confident answer; Grad-CAM called "Located issue" | Validation-chosen confidence threshold with "uncertain" fallback; Grad-CAM described as regions influencing the prediction |

Why the keypoint check matters: while building the notebook, a split based on embedding similarity alone left 33 to 44% of test photos with a copy of the same photo in training (rotated, cropped or colour-shifted). With the keypoint check, it was 2 to 4%. Lowering the similarity threshold instead merges unrelated photos into groups of hundreds.

Experiment A reproduces v1's model and settings on the clean split. Comparing its score with v1's 92% shows how much of that figure came from leakage.

## Using the trained model in your app

Copy `build_model`, `load_image`, `load_classifier` and `predict_image` from the notebook (sections 4.2, 6.2 and 10) into your app, then:

```python
model, bundle = load_classifier("dental_classifier.pt")
result = predict_image(model, bundle, "photo.jpg")
# {'label': 'caries' or None if uncertain, 'confidence': 0.93, 'uncertain': False,
#  'top3': [...], 'message': 'AI screening result only, not a diagnosis. ...'}
```

`predict_image` uses the same `load_image` preprocessing as training (EXIF rotation fix, `max_side` shrink), then resizes, normalises and applies the saved confidence threshold. `load_classifier` does not download ImageNet weights, because the checkpoint replaces them. Show `message` to the user every time.

## Troubleshooting

| Symptom | Fix |
|---|---|
| Device shows `no GPU` | `Runtime > Change runtime type > T4 GPU`, then `Runtime > Restart and run all` |
| Kaggle `401` or `403` | Token wrong or expired. Create a new one. For a Colab secret, check the name is exactly `KAGGLE_API_TOKEN` and notebook access is on |
| `CUDA out of memory` | Set `batch_size=16` in `CFG`, or remove the ConvNeXt experiment |
| Session disconnected mid-training | Rerun all. Use section 12 Option B next time to save to Drive |
| "Validation accuracy never reached 95%" | The fallback threshold of 0.90 is used. Lower `target_selective_acc` (for example 0.90) or improve the model |
| Running locally on Windows | Works on CPU but slowly. `num_workers` is set to 0 automatically on Windows |

## Notes for IT2226 assessment

- **AI Use Log.** This notebook and README were produced with an AI assistant (Kiro) and committed as one bulk import. Record that in your log. Commit your own edits separately so reviewers can tell them apart, and log what you checked (leakage asserts, near-duplicate panels, shortcut table, test metrics).
- **Live defence.** Be ready to explain why the v1 transform line was a bug, why the split is grouped and how the keypoint check works, why the test set is evaluated only once, and where to change the confidence threshold (`CFG["target_selective_acc"]` and section 8).
- **Ethical AI checklist.** Section 13 of the notebook maps outputs to checklist questions Q2, Q5, Q9, Q10 and Q11.
- **Limitations.** Small test counts for the minority classes, possible label noise, different shots of the same mouth possibly crossing splits (no patient IDs in the dataset), and web photos that may not match what real users photograph.
