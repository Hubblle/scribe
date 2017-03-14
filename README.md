Scribe: Realist Handwriting in Tensorflow
=======
See [blog post](https://greydanus.github.io/2016/08/21/handwriting/)

Jupyter Notebooks
--------
For an easy intro to the code (along with equations and explanations) check out these Jupyter notebooks:
* [inspecting the data](https://nbviewer.jupyter.org/github/greydanus/scribe/blob/master/dataloader.ipynb)
* [sampling from the model](https://nbviewer.jupyter.org/github/greydanus/scribe/blob/master/sample.ipynb)

Getting started
--------
Make sure you have all the dependencies (listed below) installed. If you want to run the Jupyter notebooks, you should also `pip instal jupyter`
* download the repo
* navigate to the repo in bash
* download and unzip pretrained model: `wget http://caligari.dartmouth.edu/~sgreydan/scribe/saved.tgz && tar xvfz saved.tgz`

Now you have two options:
1. Run the sampler in bash: `mkdir -p ./logs/figures && python run.py --sample --tsteps 256`
2. Open the sample.ipynb jupyter notebook and run cell-by-cell (it includes equations and text to explain how the model works)


About
--------
This model is trained on the IAM handwriting dataset and was inspired by the model described by the famous 2014 Alex Graves [paper](https://arxiv.org/abs/1308.0850). It consists of a three-layer recurrent neural network (LSTM cells) with a Gaussian Mixture Density Network (MDN) cap on top. I have also implemented the attention mechanism from the paper which allows the network to 'focus' on character at a time in a sequence as it draws them.

The model at one time step looks like this: 
![Rolled model](static/model_rolled.png?raw=true)

Unrolling in time, we get
![Unrolled model](static/model_unrolled.png?raw=true)

I've implemented the attention mechanism from the paper:
![Attention mechanism](static/diag_window.png?raw=true)

Dependencies
--------
* All code is written in python 2.7. You will need:
 * Numpy
 * Matplotlib
 * [TensorFlow 1.0](https://www.tensorflow.org/install/)
