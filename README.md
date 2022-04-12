# plates recognition practice

## Tools and Libraries
- Python==3.6
- Keras==2.3.1
- Tensorflow==1.14.0
- Numpy==1.17.4
- Matplotlib==3.2.1
- OpenCV==4.1.0
- sklearn==0.21.3

# model
- MobileNet
    - is a pre-trained model that widely used in many real-world applications which includes object detection, fine-grained classifications, face attributes, and localization.
    - MobileNets_character_recognition.json (pre-trained architecture)
    - License_character_recognition_weight.h5 (pre-trained weights)
    - license_character_classes.npy(pre-trained labels)

- Wpod_net
    - is a pre-trained model that proposed to detect plates in a variety of different distortions.
    Using the pre-trained model named Wpod-Net to detect and extract license plates of vehicles images.

    - Wpod-net.h(saved weights of our trained network)
    - Wpod-net.json(model architecture)

##

- Convert to 255 scale. 
	- Extracted license image from Wpod-Net is interpreted as 0–1 scale, thus we need to convert it to 8-bit scale as standard image.
- Convert to grayscale. 
	- Color plays an negligible role to understand the license plate, thus we can remove it to optimize computational power.
- Blur image. 
	- Blur technique is performed to remove noise and irrelevant information. In the example code, I used Gaussian Blur with kernel size of (7,7) but this value can be tuned depending on your image. The higher of the kernel size, the less noise but more information is lost."
- Image thresholding. 
	- We set a threshold so that any smaller pixel value than it would be converted to 255 and vice versa. This type of thresholding is called inverse binary thresholding . In the example code, I used threshold value of 180, this value can be modified to be more compatible with your image.
- Dilation. 
	- This is a technique to increase the white region of the image. By implementing dilation, we want to enhance the white contour of each character,"


# Model
- Attention mechanism: 
    - RNN or LSTM, neural network architectures
- Visual attention:
    - NLP domain
- OCR- Optical character recognition
    - Attention OCR:
        - As a way to solve captioning problem. Thought of as a CRNN followed by an attention decoder. 
        - First we use layers of convolutional networks to extract encoded image features. These extracted features are then encoded to strings and passed through a recurrent network for the attention mechanism to process.
        - The attention mechanism used in the implementation is borrowed from the Seq2Seq machine translation model. We use this attention based decoder to finally predict the text in our image.
    - Building your own Attention OCR model:
        - will use attention-ocr to train a model on a set of images of number plates along with their labels - the text present in the number plates and the bounding box coordinates of those number plates. The dataset was acquired from here.

        
- RAM-recurrent attention model
    - approaches the problem of attention by using reinforcement learning to model how the human eye work …The back-propagation is done using the REINFORCE policy gradient on the log-likelihood of the attention score.

- DRAM- deep recurrent attention model
    - Instead of using a single RNN, DRAM uses two RNNs - a location RNN to predict the next glimpse location and another Classification RNN dedicated to predicting the class labels or guess which character is it we are looking at in the text
    - The training is done using an accumulated reward and optimizing the sequence log-likelihood loss function using the REINFORCE policy gradient.
    - Or you can explore the Nanonets API where all you have to do is upload annotated images and let the platform handle the rest for you. More about this in the final section.

- CRNN- convolutional recurrent neural networks
    - CRNNs don't treat our OCR task as a reinforcement learning problem but as a machine learning problem with a custom loss.
    - The loss used is called CTC loss - Connectionist Temporal Classification. 
    - The convolutional layers are used as feature extractors that pass these features to the recurrent layers - bi-directional LSTMs . 


- LSTM – long short-term memory, 
	- networks are a modified version of recurrent neural networks, which makes it easier to remember past data in memory. The vanishing gradient problem of RNN is resolved here.  LSTM is well-suited to classify, process and predict time series given time lags of unknown duration. It trains the model by using back-propagation. 3 gates, input, forget, output.


- RNN- recurrent neural networks,
	-  generalization of feedforward neural network that has an internal memory. RNNs can use their internal state (memory) to process sequences of inputs
	- Advantages of Recurrent Neural Network
		- RNN can model sequence of data so that each sample can be assumed to be dependent on previous ones
		- Recurrent neural network are even used with convolutional layers to extend the effective pixel neighbourhood.
	- Disadvantages of Recurrent Neural Network
		- Gradient vanishing and exploding problems.
		- Training an RNN is a very difficult task.
		- It cannot process very long sequences if using tanh or relu as an activation function.




## Credit
MIT License
Copyright (c) 2020 Quang Nguyen
