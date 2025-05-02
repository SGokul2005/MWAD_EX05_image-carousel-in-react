# MWAD_EX05_image-carousel-in-react
## Date:2.05.2025

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM
ImageCarousel.js
```
import React, { useState, useEffect } from 'react';
import './ImageCarousel.css';

// Import local images
import img1 from './images/img1.jpg';

const images = [img1];

const ImageCarousel = () => {
  const [index, setIndex] = useState(0);

  const nextImage = () => {
    setIndex((index + 1) % images.length);
  };

  const prevImage = () => {
    setIndex((index - 1 + images.length) % images.length);
  };

  useEffect(() => {
    const timer = setInterval(nextImage, 3000);
    return () => clearInterval(timer);
  }, [index]);

  return (
    <div className="carousel-container">
      <img src={images[index]} alt={`Slide ${index + 1}`} className="carousel-image" />
      <div className="buttons">
        <button onClick={prevImage}>Previous</button>
        <button onClick={nextImage}>Next</button>
      </div>
    </div>
  );
};

export default ImageCarousel;
```
ImageCarousel.css
```
.carousel-container {
  width: 600px;
  margin: 40px auto;
  text-align: center;
}

.carousel-image {
  width: 100%;
  height: auto;
  border-radius: 10px;
}

.buttons {
  margin-top: 15px;
}

button {
  padding: 10px 20px;
  margin: 0 10px;
  font-size: 16px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}
```
App.js
```
import React from 'react';
import ImageCarousel from './ImageCarousel';

function App() {
  return (
    <div>
      <h2 style={{ textAlign: 'center' }}>Image Carousel (Local Images)</h2>
      <ImageCarousel />
    </div>
  );
}

export default App;
```


## OUTPUT


## RESULT
The program for creating Image Carousel using React is executed successfully.
