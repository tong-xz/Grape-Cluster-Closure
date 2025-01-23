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
And if you are using Nvidia GPU, which is also a must, please configure the GPU following this [tutorial]<https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html>

```bash
docker build -t grape .
docker run --gpus all -it grape 
```
## Training


```bash
cd PaddleSeg
python tools/train.py --config <config file absoulte path>
```

**Docker:**
```bash
python3 PaddleSeg/tools/train.py --config psp-docker.yml 
```

## Evaluation

```bash
cd PaddleSeg
python tools/val.py --config <config file absoulte path> --model_path <model path>
```
**Docker:** 
```bash
python3 PaddleSeg/tools/val.py --config psp-docker.yml --model_path PaddleSeg/output/<iter folder>/model.pdparams
```

The model evaluation result will be shown in the format below:
<img src="assets/eval_result.png" alt="alt text" width="75%">


## Inference
When training process finished, there will be a new folder named `output` in the PaddleSeg folder. Select the `model.pdparams` in the suitable iteration folder.
```bash
cd <root path>
python inference.py --config <config file absoulte path> --model_path <model path> --image_path <img directory> --save_dir <save directory>
```

**Docker:** 
```bash
python3 PaddleSeg/tools/inference.py --config psp-docker.yml --model_path PaddleSeg/output/<iter folder>/model.pdparams --image_path data/example.jpg --save_dir results
```
