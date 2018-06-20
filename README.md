# Image Plagarism Detection
Plagiarism is any identical or lightly-altered use of one's own or someone else’s work (ideas, texts, structures, images, plans, etc.) without adequate reference to the source. There are two main types of plagiarism as Text Based Plagiarism and Image Based Plagiarism. Text Based Plagiarism includes ‘copying textual information available from internet or other resources without proper permission and presenting it as their own”. Image Based plagiarism includes "copying an image or portions of an image from the Internet or from classroom resources without permission or proper acknowledgment.” The Internet is a source by which you may get everything. Anybody can use it. If you are a photographer and your images are used by another without your permission, it shall not take you happy. It is necessary to keep track of your photographs. Plagarism detection of the image is necessary to avoid any potential copyright issues in the future.


## Getting Started

### Prerequisites

- [Python](http://www.python.org)
- [Numpy](#)
- [Scikit-image](#)
- [Pillow](#)

### Installing

- Install [Python](http://www.python.org)
- Install [Numpy](#)
- Install [Scikit-image](#)
- Install [Pillow](#)


## Built With

* [Python](#)

### How it works?
Normalized cross-correlation is used to solve this.  Cross-Correlation is a standard method for calculating how closely two series or values are correlated or resemble each other, and it is commonly used for pattern recognition. In the case of image which is represented as a two dimensional array of pixels, cross-correlation is performed by sliding the template image across the larger search image. At each location the algorithm calculates an integral to determine how closely the template image correlates with that section of the search image. The match template funciton also normalizes these results to account for differences between analyzing very bright or very dark pictures. The result of this is a two dimensional array of values representing how closely the template and the search image match at each location. A higher correlation value means that the template image matches more closely at that point. If we receive a high correlation value we can be pretty sure that the template image is  a subset of the other in that location. Below is the procedure we follow:
-	We designate one image file as original, and the other as the template.
-	First, a quick check is performed to verify that the template image is in fact smaller than original image, which is a pretty obvious requirement for it to be a subset of the original image.
-	Once the image pairs pass that check, a comparision will be made against size with threshold we set for the images we want to execute the match template function on. If the images are larger than our threshold then they will be resized them down to a more reasonable to reduce the amount of processing that the match template function will need to do.
-	Images will be converted to grayscale to save processing time. If we analyze  the images in their original color format then we would need to perform each calulation there times. Once for each of the red, green and blue channels. By converting to grayscale here we’re effectively reducing the amount of processing by a third for certain calculations.
-	After the images have been resized and converted to grayscale, we use the match template function to determine where they most closely match by finding the maximum correlation value in the output array from the match template function. 
-	Using that information,  we return to original full size image and crop out the section of that image which is the size of the template image.  
-	Now, we’ll compare the subset from the original image, and the template image to determine if they are same.
-	Using an image channel operation we can calculate the difference between our new subset and the template image. In the ideal case if the template was a subset of the original image then output of this operation would be zero or completely black.
-	To determine if this difference between the two images is close enough to zero to be considered a match, we’ll calculate the histrogram of this difference array.
-	To determine whether or not the histogram of that difference array is close enough to zero to be considered a match we can calculate the root means squared or RMS value. The RMS value of a sequence is the quadratic mean which is a statistical method for finding the average magnitude of the values.
- A comparision of this RMS value should be made with threshold value and if it is low enough then we consider the two images to be a match, and thus the template image was indeed of the original image. 


## Authors

* **Prathap Puppala**  -  [www.prathappuppala.com](https://www.prathappuppala.com)
