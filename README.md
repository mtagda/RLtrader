# RLtrader
Deep Reinforcement Learning agent for trading

## About the code
This code is a modification of the repository https://github.com/PacktPublishing/Deep-Reinforcement-Learning-Hands-On/tree/master/Chapter08 discussed in the book _"Deep Reinforcement Learning Hands-On"_ by Max Lapan.

## Data for training
The folder _data_ contains sample Bitcoin historical data

## How to run the code
### Training 
To start the training, you need to pass training data with the --data option, which could be an individual CSV file of the whole directory with files. 
By default, the training module uses Bitcoin data for H1 2017 (file data/bitcoin_train.csv). 
For the validation data, there is an option --valdata , which takes Bitcoin H2 2017 data by default. 
Another required option will be -r, which is used to pass the name of the run. This name will be used in the TensorBoard run name and to create
directories with saved models.

Please note that during training, we have several charts in TensorBoard showing us how the training is going. 
In order to see those charts, you should execute the following command

```
tensorboard --logdir runs --host localhost
```
Usually TensorBoard runs then at http://localhost:6006/

### Running the model

During the training, our code saves models for later experiments. It does this
every time the mean Q-values on our held-out states set updates the maximum.
There is a tool which loads the model, trades on prices you’ve provided to it with
the command-line option and draws the plots with the profit change over time.
The tool is called run_model.py and the options that the tool accepts are as follows:

* -d : This is the path to the quotes to use. 
* -m : This is the path to the model file. By default, the training code saves
it in saves dir.
* -b : This shows how many bars to pass to the model in the context. It has
to match the count of bars used on training, which is 10 by default and
can be changed in the training code.
* -n : This is the suffix to be prepended to the images produced.
* --commission : This allows you to redefine the broker’s commission,
which has a default of 0.1%.

