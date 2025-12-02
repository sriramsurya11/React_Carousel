# Ex05 Image Carousel
## Date:

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
```
app.js
import React from 'react';
import ImageCarousel from './imageCarousel';

function App() {
  const images = [
    "https://images.unsplash.com/photo-1529626455594-4ff0802cfb7e",
    "https://images.unsplash.com/photo-1519125323398-675f0ddb6308",
    "https://images.unsplash.com/photo-1507525428034-b723cf961d3e"
  ];

  return (
    <div className="App">
      <ImageCarousel images={images} />
    </div>
  );
}

export default App;
```
```
image.js
import React, { useState, useEffect, useCallback } from 'react';

const images = [
  'https://images.unsplash.com/photo-1503023391225,
  'https://images.unsplash.com/photo-1534528741702,
  'https://images.unsplash.com/photo-1520813792240'
];

function ImageCarousel() {
  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = useCallback(() => {
    setCurrentIndex((prevIndex) => (prevIndex + 1) % images.length);
  }, []);

  const prevImage = () => {
    setCurrentIndex((prevIndex) =>
      (prevIndex - 1 + images.length) % images.length
    );
  };

  useEffect(() => {
    const interval = setInterval(() => {
      nextImage();
    }, 3000);

    return () => clearInterval(interval);
  }, [nextImage]);

  return (
    <div style={{ textAlign: 'center' }}>
      <h1>React Image Carousel</h1>
      <img
        src={images[currentIndex]}
        alt="carousel"
        style={{ width: '400px', borderRadius: '10px' }}
      />
      <br />
      <button onClick={prevImage}>Previous</button>
      <button onClick={nextImage} style={{ marginLeft: '10px' }}>
        Next
      </button>
    </div>
  );
}

export default ImageCarousel;
```
```
index.css
/* Reset and Font */
body {
  margin: 0;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background: linear-gradient(135deg, #f8f9fa, #d6e4f0);
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

/* Carousel Container */
.carousel-container {
  background-color: #ffffffdd;
  padding: 40px;
  border-radius: 16px;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
  text-align: center;
}

/* Title */
.carousel-container h1 {
  font-size: 2.5rem;
  margin-bottom: 30px;
  color: #2c3e50;
}

/* Image Styling */
.carousel-container img {
  width: 100%;
  max-width: 500px;
  height: auto;
  border-radius: 16px;
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.25);
  transition: transform 0.3s ease;
}

.carousel-container img:hover {
  transform: scale(1.03);
}

/* Button Container */
.button-container {
  margin-top: 20px;
}

/* Navigation Buttons */
.button-container button {
  background-color: #2c3e50;
  color: white;
  border: none;
  padding: 12px 24px;
  margin: 0 10px;
  border-radius: 8px;
  cursor: pointer;
  font-size: 1rem;
  transition: background-color 0.3s ease;
}

.button-container button:hover {
  background-color: #34495e;
}
```

## OUTPUT

![444631781-49d4b74a-8189-4896-930e-3f0b8010bad3](https://github.com/user-attachments/assets/1708176e-c504-45e3-829b-9a2981d08a17)

![444631809-5a1e663e-9386-4762-aa79-efb55aa01aa3](https://github.com/user-attachments/assets/96a41660-e7c0-4ccc-9e79-79a94fa274fc)



## RESULT
The program for creating Image Carousel using React is executed successfully.
