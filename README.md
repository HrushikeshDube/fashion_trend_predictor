# FashionTrends

This project focuses on predicting fashion trends over time using machine learning. The current implementation classifies different types of clothing (Shirts, Skirts, Pants, Dress) based on images collected from chictopia.com. The model is built using Keras and is trained on the web-scraped images.

### Purpose
Predicting fashion trends can help retailers improve logistics for inventory and shipping. Retailers currently rely on sales data and fashion shows/blogs to anticipate trends. This project aims to add another layer of analytics by potentially predicting demand using machine learning models trained on images and social media data.

### Current Status
This project was developed as part of the Maverick team in DSC at the University of Texas at Dallas. While development is paused due to team members leaving, I plan to revisit the project during the summer. The code is available publicly on GitHub so others can benefit from it.

---

## Project Structure

The project is divided into the following components:

1. **`webscraper.py`**  
   Scrapes images and tags from chictopia.com.

2. **`csvDownload.py`**  
   Downloads the images scraped by `webscraper.py`.

3. **`preprocessing.py`**  
   Preprocesses the downloaded images.

4. **`FashionTrends.py`**  
   Trains the machine learning model using preprocessed images.

---

## How It Works

### Data Collection
- Web scraping is done using [BeautifulSoup](https://pypi.org/project/beautifulsoup4/).
- Images are downloaded and stored in a CSV format.

### Preprocessing
1. **Background Removal**  
   Background is removed from the images using [DeepLabv3+](https://github.com/bonlime/keras-deeplab-v3-plus).

2. **Resizing and Clustering**  
   The images are resized, and K-means clustering (with 4 clusters) is applied using [Scikit-learn’s KMeans](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html).

3. **Final Output**  
   After preprocessing, a 2D NumPy array is saved for each image, with cluster values based on the clustering. This processed data is used for training.

---

### Model Training
The model is a Convolutional Neural Network (CNN) with the following architecture:
- 2 convolutional layers
- 2 dropout layers
- 1 softmax layer
- Optimizer: Adadelta

The model is trained using the preprocessed images and their corresponding cluster arrays.

---

### Future Improvements
- **Dataset Expansion:** The current dataset is small (~1200 images). Expanding the dataset will improve the model’s performance.
- **Generative Adversarial Networks (GANs):** Incorporating GANs could help enhance the classification results.

---

## Disclaimer
This is an experimental project, and the results should not be taken as definitive. There may be better methods and techniques that I have yet to explore.
