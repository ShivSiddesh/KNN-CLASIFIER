# KNN-CLASIFIER
3 CLASS ANIMALS CLASSIFICATION USING K NEAREST NEIGHBOR CLASSIFIER

STEPS INVOLVED IN DESIGN OF KNN CLASSIFIER

1.	GATHER THE DATASET 
•	I created a folder in the jupyter notebook and named it as KNN_DETECTION, where I created three subfolders to store the images of dogs, cats and panda
•	I opened a new PYTHON 3 notebook and called it as knn_ipynb, where it contains the entire code for KNN Classifier
•	I have imported all the necessary dictionaries which are required for the execution of the program
•	I have used os.walk to run over all my sub-folders which contain dogs, cats and pandas to store in a single file that contains filenames called as fileNameList, and all my images in one file as imageList
•	So my fileNameList and imageList contains 3000 filenames and images respectively 
•	I have used cv2.resize to resize my images into size 32*32, containing the 3 RGB channels which implies that each image is represented by 32*32*3=3072 integers and store it in resized_image  
•	Since my resized_image is a row vector, I want to create a matrix where all my RGB elements of a single image should be in single row, and hence for all my 3000 images, and I append all my images into a single list called as finalList 
•	The size of my finalList is 3000 rows and 3072 columns (3000*3072)


2.	SPLIT THE DATASET 
•	Now i have to label my dataset into cats, dogs and panda. So i use 
0 – cats, 1- dogs and 2- panda, and I append these values at the end of my list for all the 3000 images, so my total length for each image will be 3073 
•	Now I split my data into 3 different sets called as Train, Validate and Test where train contains 70% my data, validate 10% and test 20% (All the data sets contain equal number of cats, dogs and panda)
•	So train has 2100 images, validate- 300 images and test- 600 images 


3.	TRAIN THE CLASSIFIER 
•	Here I have trained my classifier using the logic that was explained in the class 
•	I have used my validation data set and compare it with my train data to get the distance i.e. an integer value and update it in my matrix
•	I have named the matrix as distance and its size is 300*2100 (that is each image in my validation set of 300 gets compared to the train set of 2100 and form the distance to produce a 300*2100 matrix)
•	Now I have selected the various values of K and got the minimum distance for each value of k (that means if K= 100, I have taken 100 smallest distances in each row of the distance matrix)
•	I have used np.argsort(arr) to get the minimum distance based on the value of k 
•	And I have stored all my index positions into an array called Index
•	Now using my index, I can get back my image in the train dataset, using the image in the train dataset I will extract the last integer that I appended it as my label, using the value of my label I can get what animal is predicted i.e. 0 for cats, 1 for dogs and 2 for panda 
•	I will append all the predicted animals into a list called as pred
•	And hence pred list will have the matrix of the form 300*K
•	Now I use the confusion_matrix which is an inbuilt dictionary to get the confusion matrix 
•	The confusionMatrix is the file which contains 3*3 matrix containing 3 columns and 3 rows i.e actual classes and predicted classes, and the classes are cats, dogs and pandas (for all the values of K)
•	From the confusion matrix we calculate the accuracy from the values of true positive, true negative, false positive and false negatives 
•	For the various values of K we get the accuracies, so we need to find the K which has the highest accuracy 


4.	EVALUATE 
•	After finding the best value of k, use that value of k to evaluate the test images 
•	After evaluating, find the accuracy, precision, recall and f-measure 





5.	RESULTS
•	The best value of K was found to be 50
•	Accuracy of 65.78%
•	The value of precision is 48.67%
•	The value of recall is 48.67%
•	The value of f_measure is 48.67%
