# Brain-Tumour-Classification
In this project, BraTs-18 and BraTs-19 dataset has been used. The aim of this project to recognize High Grade Glioma(HGG) and Low Grade Gliom(LGG) in 3D dataset. Gliomas are most common type of tumours, and they are classified in four different categories by World health organization(WHO). In my project, I used flair, t1, t2, and t1ce. The dataset has 1208 examples in total. There are 966 training examples and 242 validation examples. Which means almost 80% of the data is reserved for training and approximately 20% of the data has been used for validating the model. Equal number of examples has been selected both for HGG and LGG examples. The dataset is in NIFTI files.

A preprocessing and data preparation function has been written to prepare BraTs-18 and BraTs-19 dataset. This function will select t1, t2, flair, and t1ce from the dataset, and it will discard seg file. In addtion, it will read all the nii.gz files from both HGG and LGG folders, following that it will label the dataset. The function will convert the dataset into training and validation dictionaries by shuffling the contents of the dataset.

After reading the dataset, data transform function has been used to transform the 3D images and to apply data augmentation to the dataset. It's common to preprocess and augment the dataset for training the model. Data augmentation adds diversity to the dataset, and makes the model robust for the future data it will see during inference. I used Random rotation, translation, and scaleintensity options to enlarge our training set. The small dataset causes overfitting, so adding more examples helps minimizing overfitting, it's not always easy to get medical dataset, however, data augmentation is very cheap and realible option.

![sample_slice_hgg_](https://user-images.githubusercontent.com/61932757/151831134-7715f5f1-f0ed-415a-8f0a-b16ab96acea4.png)
![augmented_slice1](https://user-images.githubusercontent.com/61932757/151831399-a76857d6-99ea-4e8e-a87b-8f4aa8d93f19.png)
Fig1: sample slices in a volume

After preparing and preprocessing the dataset, DenseNet121 has been used for training. A DenseNet is a sort of convolutional neural network that employes dense connections between its layers, through Dense Blocks, where we connect all layers directly with each other. To maintain the feed-forward nature, each layer obtains additional inputs from all preceding layers and passes on its own feature-maps to all subsequent layers. For more, please read DenseNet Paper.

![densenet](https://user-images.githubusercontent.com/61932757/151832451-392c1865-ec4a-4d76-a403-9c0017a13f98.png)
Fig2: DenseNet 

The model has acheived 94.5% validation accuracy, and AUC was 98.3%. it's performance could further be improved by tuning hyperparameters values, for instance, learning rate, batch size, number of epochs. And applying optimal data augmentation options.

