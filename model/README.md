# Recommendation model

[Project](../README.md) · [한국어](README.ko.md) · [Model decisions and evaluation](../docs/wiki/Model.md)

The served recommender is **Multi-DAE**, a denoising autoencoder mapping a preferred-item vector to catalog scores. This folder also contains Multi-VAE; its presence does not mean it was deployed.

## Files

- `AE_model/Multi_DAE.py`: Multi-DAE architecture.
- `AE_model/Multi_VAE.py`: variational-autoencoder alternative.
- `AE_model/dataloader.py`: interaction loading.
- `AE_model/train.py`: training and checkpoint selection.
- `AE_model/inference.py`: inference.
- `AE_model/args.py`, `utils.py`: configuration and utilities.

## Historical workflow

1. Place updated interactions at `backend/data/train.tsv`.
2. From `model/AE_model/`, run `python train.py`.
3. The best recall checkpoint is saved to `model/saved_model/best_model.pt`.
4. From `gcp/`, run `python main.py --mode 0` to upload it.
5. Other developers run `python main.py` from `gcp/` to download it for serving.

Data and checkpoints are not bundled. See [GCP setup](../gcp/README.md) for private configuration.

## Evaluation lesson

NDCG@10 and Recall@10 plateaued while service recommendations remained similar across users. Catalog coverage exposed this failure. Longer training improved coverage and subsequently accuracy: an evaluation/training intervention, **not a new diversity loss**.
