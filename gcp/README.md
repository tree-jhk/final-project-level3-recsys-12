# Model-artifact transfer — Google Cloud Storage

[Project](../README.md) · [한국어](README.ko.md)

The trained model was approximately **270 MB**, too large for ordinary GitHub tracking. Cloud Storage replaced unreliable manual transfer and helped align training and serving checkpoints.

## Historical setup

```bash
pip install --upgrade google-cloud-storage
```

Place your own authorized service-account key in `gcp/keys/` as expected by configuration. The original team obtained keys from a private workspace. Do not commit keys.

From `gcp/`:

```bash
# Download into backend/inference.
python main.py

# Upload a trained checkpoint.
python main.py --mode 0
```

`gcp_args.py` defines arguments; `create_bucket.py` and `utils.py` provide utilities. Check bucket names and checkpoint paths first.

Web developers could retrieve new checkpoints when needed. This provided a building block for future automation, **not evidence of a fully deployed Airflow retraining pipeline**.
