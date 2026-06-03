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
JSX FILE 
```
import React, { useState } from "react";
import "./ImageCarousel.css";

function ImageCarousel() {
  const images = [
    "https://picsum.photos/id/1015/800/400",
    "https://picsum.photos/id/1016/800/400",
    "https://picsum.photos/id/1018/800/400",
    "https://picsum.photos/id/1020/800/400"
  ];

  const [current, setCurrent] = useState(0);

  const nextImage = () => {
    setCurrent((current + 1) % images.length);
  };

  const prevImage = () => {
    setCurrent(
      current === 0 ? images.length - 1 : current - 1
    );
  };

  return (
    <div className="container">
      <h1>Image Carousel</h1>

      <div className="carousel">
        <button onClick={prevImage}>◀</button>

        <img
          src={images[current]}
          alt="carousel"
        />

        <button onClick={nextImage}>▶</button>
      </div>

      <footer>
        <p>Name: THARUN</p>
        <p>Register Number: YOUR_REGISTER_NUMBER</p>
      </footer>
    </div>
  );
}

export default ImageCarousel;
```
CSS FILE 
```
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family:Arial, sans-serif;
}

.container{
  min-height:100vh;
  background:#f4f4f4;
  text-align:center;
  padding:40px;
}

h1{
  margin-bottom:30px;
}

.carousel{
  display:flex;
  justify-content:center;
  align-items:center;
  gap:20px;
}

.carousel img{
  width:800px;
  max-width:90%;
  height:400px;
  object-fit:cover;
  border-radius:10px;
  box-shadow:0 0 10px rgba(0,0,0,0.3);
}

.carousel button{
  padding:15px 20px;
  font-size:20px;
  border:none;
  background:#007bff;
  color:white;
  cursor:pointer;
  border-radius:5px;
}

footer{
  margin-top:40px;
  padding:20px;
}
```
APP.JSX
```
import ImageCarousel from "./ImageCarousel";

function App() {
  return <ImageCarousel />;
}

export default App;
```

## OUTPUT
<img width="662" height="398" alt="image" src="https://github.com/user-attachments/assets/7afa5425-3f39-4172-9b5f-9dea76ab5316" />


## RESULT
The program for creating Image Carousel using React is executed successfully.
