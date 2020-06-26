# STUDENT CODE-IN

****About SCI****

Student Code-In is a global program that helps students grow with Open Source Contribution. It is a 2 months long Open-Source initiative which provides you the best platform to improve your skills and abilities by contributing to vast variety of Open Source Projects Projects. In this, all the registered participants would get an exquisite opportunity to interact with the mentors and the Organizing Team. 


<p align="center">
  <a href="https://scodein.tech/">
    <img src="https://avatars1.githubusercontent.com/u/63442932?s=200&v=4" alt="Logo">
  </a>

# Image Captioning Project

In this project, I design and train a CNN-RNN (Convolutional Neural Network - Recurrent Neural Network) model for  automatically generating image captions. The network is trained on the Microsoft Common Objects in COntext [(MS COCO)](http://cocodataset.org/#home) dataset. The image captioning model is displayed below.
![Image Captioning Model](images/cnn_rnn_model.png?raw=true) [Image source](https://arxiv.org/pdf/1411.4555.pdf)

## Dataset Visualization
![Image Captioning Model](images/coco-examples.jpg?raw=true)


## Algorithm Visualization
![Encoder](images/encoder.png?raw=true)
### It is the first part part of Model i.e Encoder. It is a CNN Algorithm.
![Decoder](images/decoder.png?raw=true)
### It is second part of Model i.e Decoder. It is a LSTM Algorithm. 
![Encoder-Decoder](images/encoder-decoder.png?raw=true)
### Complete Visualization of how algorithm will work completely.

## Generating Image Captions

Here are some predictions from my model.

### Good results
![sample_172](samples/sample_172.png?raw=true)<br/>
![sample_440](samples/sample_440.png?raw=true)<br/>
![sample_457](samples/sample_457.png?raw=true)<br/>
![sample_002](samples/sample_002.png?raw=true)<br/>
![sample_029](samples/sample_029.png?raw=true)<br/>
![sample_107](samples/sample_107.png?raw=true)<br/>
![sample_202](samples/sample_202.png?raw=true)

## File Descriptions
- **0_Datasets.ipynb:** The purpose of this file is to initialize the COCO API and visualize the dataset. [The Microsoft Common Objects in COntext (MS COCO) dataset](https://cocodataset.org/#home) can be accessed using the COCO API. The API has methods like "getAnnIds", "loadImgs" etc to access the images and annotations. In the 0_Datasets.ipynb file we load the instance annotations and captions annotations into memory using COCO API. Then we plot a random image from the dataset, along with its five corresponding captions. This file helps in understanding the working of the COCO API and the structure of the dataset.

- **1_Preliminaries.ipynb:** The purpose of this file is to load and pre-process data from the COCO dataset and also design a CNN-RNN model for automatically generating image captions. We use the [Data loader](https://pytorch.org/docs/master/data.html#torch.utils.data.DataLoader) provided by pytorch to load the COCO dataset in batches. We initialize  the data loader by using the "get_loader" method in data_loader.py. The "get_loader" function takes as input a number of arguments like "transform", "mode", "batch_size" etc. The __getitem__ method in the CoCoDataset class is used to preprocess the  image-caption pairs before incorporating them in a batch. For caption preprocessing we initialize an empty list and append an integer to mark the start of a caption. We use a special start and end word to mark the beginning and end of a caption. We append integers to the list that correspond to each of the tokens in the caption. Finally, we convert the list of integers to a [PyTorch tensor](https://pytorch.org/docs/master/tensors.html) and cast it to long type. To generate batches of training data, we begin by first sampling a caption length (where the probability that any length is drawn is proportional to the number of captions with that length in the dataset). Then, we retrieve a batch of size batch_size of image-caption pairs, where all captions have the sampled length. Once our batches are ready we import and instantiate the CNN encoder from the model.py file. The encoder uses the pre-trained ResNet-50 architecture (with the final fully-connected layer removed) to extract features from a batch of pre-processed images. The output is then flattened to a vector, before being passed through a Linear layer to transform the feature vector to have the same size as the word embedding. Then we import the RNN decoder from model.py. It outputs a PyTorch tensor with size [batch_size, captions.shape[1], vocab_size]. The output is designed such that outputs[i,j,k] contains the model's predicted score, indicating how likely the j-th token in the i-th caption in the batch is the k-th token in the vocabulary.

##  💥 How to Contribute?

- Take a look at the Existing Issues or create your own Issues!
- Wait for the Issue to be assigned to you after which you can start working on it.
- Fork the Repo and create a Branch for any Issue that you are working upon.
- Create a Pull Request which will be promptly reviewed and suggestions would be added to improve it.
- Add Screenshots to help us know what this Script is all about.

