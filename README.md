# Grape-Cluster-Closure
Manushi's work tuned version

## Environment
**Firstly**, please change all the following variables to your own values in the `psp2.yml` file:
- `dataset_root`: the absolute path to the dataset
- `train_path`: the absolute path to the train.txt file
- `val_path`: the absolute path to the val.txt file
- `batch_size`: controls how many data samples to train on each iteration
- `iters`: controls how many iterations to train

**Secondly**, you will need to install [docker]<https://docs.docker.com/engine/install/ubuntu/> on your machine, which I highly recommend using the Ubuntu system. 


```bash
docker build -t grape .
docker run --gpus all -it grape 
## Training

```bash
cd PaddleSeg
python tools/train.py --config <config file absoulte path>
```

**For example:** `python3 ./tools/train.py --config /home/xz/Dev/Grape-Cluster-Closure/psp2.yml`

## Evaluation

```bash
cd PaddleSeg
python tools/val.py --config <config file absoulte path> --model_path <model path>
```
**For example:** `python3 tools/val.py --config /home/xz/Dev/Grape-Cluster-Closure/psp2.yml --model_path /home/xz/Dev/Grape-Cluster-Closure/PaddleSeg/output/iter_1000/model.pdparams`


The model evaluation result will be shown in the format below:
<img src="assets/eval_result.png" alt="alt text" width="75%">


## Inference
When training process finished, there will be a new folder named `output` in the PaddleSeg folder. Select the `model.pdparams` in the suitable iteration folder.
```bash
cd <root path>
python inference.py --config <config file absoulte path> --model_path <model path> --image_path <img directory> --save_dir <save directory>
```

**For example:** `python ./tools/inference.py --config /home/xz/Dev/Grape-Cluster-Closure/psp2.yml --model_path /home/xz/Dev/Grape-Cluster-Closure/PaddleSeg/output/iter_1000/model.pdparams --image_path data/example.jpg --save_dir results`
