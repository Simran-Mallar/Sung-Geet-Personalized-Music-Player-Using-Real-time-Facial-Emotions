# Sung-Geet: Personalized Music Player Using Real-time Facial Emotions

ABSTRACT
Music recommendation systems have ample choice of songs and genres for a user to listen to, making it difficult for many users to make a selection. Keeping this in mind we propose a personalized emotion based music player that utilizes a person's facial expressions through a webcam to detect their emotion in real time. This approach not only personalizes the music selection process but also offers a more intuitive and interactive way for users to discover new songs and genres. When the webcam is activated, the system uses the MTCNN model for real-time emotion detection. When a face is detected, the system deploys the MobileNet model, a convolutional neural network pre-trained on the ImageNet dataset, to detect emotions, classify the emotions into different categories, and recommend music that aligns with the emotional state. 
To train the emotion detection model, the FER 2013 dataset from Kaggle is used. These images capture a wide range of emotional states, providing a rich and diverse dataset for training the emotion detection model. The diversity of the images ensures that the model is robust and capable of handling various facial expressions, lighting conditions, and facial orientations, enhancing its overall performance and reliability. Lastly, when the user's emotion is determined, the system recommends a list of songs that best match their current mood. This personalized music player provides a mix of Hindi and English songs based on their emotional state. By considering the user's current emotions, the system significantly improves the overall music recommendation experience.


I. METHODOLOGY:

A.  Data collection and preprocessing:

Data collection - For training the emotion detection model, we used the FER 2013 dataset from Kaggle consisting of black and white pictures that show different facial expressions with each one being assigned to one of the seven emotions. These images are relatively small with sizes like 48 by 48 pixels.
Data augmentation - Techniques like zooming, shearing, horizontal flipping, and rescaling were implemented.These techniques are employed to increase the effective size of the dataset by generating new variations of the existing images. Resizing pixel values to the range of [0, 1] during this process helps standardize input data, improving training stability, and thereby enhancing the overall training process.

B.  Emotion detection model:

The dataset used for training the emotion detection model was formed by using the FER 2013 dataset. The dataset consists of approximately 35000 grayscale images, out of which 28821 images were used for training and another set of validation constituted 7066 images.
Transfer learning was applied in constructing an emotion detection model using MobileNet as a pre-trained base model. This involved utilizing features learned from large datasets like ImageNet for face feature extraction. The fully connected layers of the model are then regularized using dropout to randomly disable neurons during training leading to a reduction in overfitting since it makes the network learn more solid features.
Batch normalization is done on dense layer activations in order to stabilize and speed up the training process.
Early stopping is also employed to stop training when validation loss stops decreasing hence, preventing the model from overfitting into the training data set. 
Data augmentation techniques applied helped the model to learn robust features and improve its generalization capabilities, reducing the risk of overfitting to the training data .
The use of these methods collectively improves the accuracy of the MobileNet Model for Facial Emotion Recognition while at the same time avoiding overfitting risks.

C.  Face detection model:

When the web camera is on in real-time, it detects faces and tells us what emotions are conveyed by them. 
A real-time processing loop keeps capturing frames, detecting faces, classifying emotions in those faces, and showing them with the emotion labels overlaid on top of them. 
MTCNN (Multi-task Cascaded Convolutional Network), a lightweight image classification architecture, is used to accurately detect each frame’s face and produce a bounding box of where it resides. 
A user can then exit the application gracefully after completing emotion detection using keyboard shortcuts (Ctrl + Q) which stops the webcam feed.
The final emotion is predicted out of these seven emotions: happy, angry, neutral, sad, surprise, fear, and disgust; by taking the mode of the maximum frames of emotion detected. 
The final predicted emotion is then displayed on the screen, from which the user has the option to select either Hindi or English songs, according to their preference.



