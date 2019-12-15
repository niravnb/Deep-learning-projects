# Image Captioning

- Motivation: 
	•	Self driving cars — Automatic driving is one of the biggest challenges and if we can properly caption the scene around the car, it can give a boost to the self driving system.
	•	Aid to the blind — We can create a product for the blind which will guide them travelling on the roads without the support of anyone else. We can do this by first converting the scene into text and then the text to voice. Both are now famous applications of Deep Learning. Refer this link where its shown how Nvidia research is trying to create such a product.
	•	CCTV cameras are everywhere today, but along with viewing the world, if we can also generate relevant captions, then we can raise alarms as soon as there is some malicious activity going on somewhere. This could probably help reduce some crime and/or accidents.
	•	Automatic Captioning can help, make Google Image Search as good as Google Search, as then every image could be first converted into a caption and then search can be performed based on the caption.


- Data set: Flickr 8k (containing8k images)

- Understanding the data: One of the files is “Flickr8k.token.txt” which contains the name of each image along with its 5 captions. 
- Data Cleaning: 
	•	When we deal with text, we generally perform some basic cleaning like lower-casing all the words (otherwise “hello” and 	“Hello” will be regarded as two separate words), removing special tokens (like ‘%’, ‘$’, ‘#’, etc.), eliminating words 		which contain numbers (like ‘hey199’, etc.).
	•	We consider only those words which occur at least 10 times in the entire corpus.
	•	We added two tokens in every caption as follows: startseq, endseq 


- Data Preprocessing — Images:
	•	We converted every image into a fixed sized vector which can then be fed as input to the neural network. For this purpose, we opt for transfer learning by using the VGG16 model (Convolutional Neural Network).
	•	This model was trained on Imagenet dataset to perform image classification on 1000 different classes of images. However, our purpose here is not to classify the image but just get fixed-length informative vector for each image. This process is called automatic feature engineering.

- Data Preprocessing — Captions:
	•	Prediction of the entire caption, given the image does not happen at once. We will predict the caption word by word. Thus, we need to encode each word into a fixed sized vector. 
	•	We created two Python Dictionaries namely “wordtoix” (pronounced — word to index) and “ixtoword” (pronounced — index to word). Stating simply, we will represent every unique word in the vocabulary by an integer (index). 


- Data Preparation using Generator Function:
	•	Since training data set is huge, so can not be put into RAM, we used generator_function to generate training data for each batch size.
	•	Appended zeros to each sequence to make them all of same length 34
	•	Used BLEU Score to evaluate and measure the performance of the model.


- Future work to make model better:
	•	Using a larger dataset.
	•	Changing the model architecture, e.g. include an attention module.
	•	Doing more hyper parameter tuning (learning rate, batch size, number of layers, number of units, dropout rate, batch normalization etc.).
	•	Use the cross validation set to understand overfitting.
	•	Using Beam Search instead of Greedy Search during Inference.
	
	
