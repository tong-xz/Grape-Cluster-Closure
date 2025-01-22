# Grape-Cluster-Closure
Manushi's work tuned version

## Environment
Firstly, please change all the following variables in the `psp2.yml` file:
- `dataset_root`: the absolute path to the dataset
- `train_path`: the absolute path to the train.txt file
- `val_path`: the absolute path to the val.txt file
- `batch_size`: controls how many data samples to train on each iteration
- `iters`: controls how many iterations to train

Secondly,


## Training

```bash
cd PaddleSeg
python tools/train.py --config <config file absoulte path>
```

**For example:** `python3 ./tools/train.py --config /home/xz/Dev/Qunatifying-Grapevine-Cluster-Closure-QCC-/psp2.yml`

## Inference

```bash
python inference.py --config configs/pspnet/pspnet.yaml --model_path models/pspnet/best_model/model.pdparams --image_path data/example.jpg --save_dir results
```