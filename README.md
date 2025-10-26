<img width="1919" height="1089" alt="Screenshot 2025-10-26 171813" src="https://github.com/user-attachments/assets/c4985306-450d-4036-85e1-91b915fa76fa" /># MWAD_EX05_image-carousel-in-react
## Date:26.10.25

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
carousel.jsx

import React, { useState } from "react";
import "./Carousel.css";

const images = [
  "https://paradepets.com/.image/c_fill,w_1200,h_900,g_faces:center/MTkxMzY1Nzg4NjczMzIwNTQ2/cutest-dog-breeds-jpg.jpg",
  "https://upload.wikimedia.org/wikipedia/commons/thumb/4/43/Cute_dog.jpg/2560px-Cute_dog.jpg",
  "https://dogtime.com/wp-content/uploads/sites/12/2023/07/GettyImages-1421259551-e1690237851531.jpg?w=1024",
  "https://media.istockphoto.com/id/2152301888/photo/funny-cavalier-king-charles-spaniel-dog-puppy-chewing-his-favorite-toy-while-lying-on-dog-bed.jpg?s=612x612&w=0&k=20&c=pCqERKz3mw9D9FlxG5s4Iqwcpgab18gB6FhbOXG133g="
];

const Carousel = () => {
  const [currentIndex, setCurrentIndex] = useState(0);

  const nextSlide = () => {
    setCurrentIndex((prev) =>
      prev === images.length - 1 ? 0 : prev + 1
    );
  };

  const prevSlide = () => {
    setCurrentIndex((prev) =>
      prev === 0 ? images.length - 1 : prev - 1
    );
  };

  return (
    <div className="carousel-container">
      <div
        className="carousel-slider"
        style={{ transform: `translateX(-${currentIndex * 100}%)` }}
      >
        {images.map((img, index) => (
          <div className="carousel-slide" key={index}>
            <img src={img} alt={`Slide ${index}`} />
          </div>
        ))}
      </div>

      <button className="prev-btn" onClick={prevSlide}>
        ❮
      </button>
      <button className="next-btn" onClick={nextSlide}>
        ❯
      </button>

      <div className="carousel-dots">
        {images.map((_, index) => (
          <span
            key={index}
            className={index === currentIndex ? "dot active" : "dot"}
            onClick={() => setCurrentIndex(index)}
          ></span>
        ))}
      </div>
    </div>
  );
};

export default Carousel;
```
```
carousel.css

.carousel-container {
  position: relative;
  width: 100%;
  max-width: 100vw;
  height: 100vh;
  overflow: hidden;
}

.carousel-slider {
  display: flex;
  transition: transform 0.5s ease-in-out;
  height: 100%;
}

.carousel-slide {
  min-width: 100%;
  height: 100%;
}

.carousel-slide img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

/* Buttons */
.prev-btn,
.next-btn {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background-color: rgba(0, 0, 0, 0.5);
  border: none;
  color: white;
  font-size: 2rem;
  padding: 10px;
  cursor: pointer;
  border-radius: 50%;
}

.prev-btn {
  left: 20px;
}

.next-btn {
  right: 20px;
}

.prev-btn:hover,
.next-btn:hover {
  background-color: rgba(0, 0, 0, 0.8);
}

/* Dots */
.carousel-dots {
  position: absolute;
  bottom: 20px;
  width: 100%;
  text-align: center;
}

.dot {
  display: inline-block;
  height: 12px;
  width: 12px;
  margin: 5px;
  background-color: #bbb;
  border-radius: 50%;
  cursor: pointer;
}

.dot.active {
  background-color: #fff;
}
```

## OUTPUT
<img width="1919" height="1089" alt="Screenshot 2025-10-26 171813" src="https://github.com/user-attachments/assets/397ff9d9-a710-4b53-8fc1-991640e6004f" />

<img width="1919" height="1094" alt="Screenshot 2025-10-26 171824" src="https://github.com/user-attachments/assets/25b50e21-0fe4-4860-8524-7e4e7166cc1c" />
<img width="1919" height="1088" alt="Screenshot 2025-10-26 171835" src="https://github.com/user-attachments/assets/a1bbb593-bf85-4c6c-bf7e-b1010e669d20" />
<img width="1919" height="1089" alt="Screenshot 2025-10-26 171846" src="https://github.com/user-attachments/assets/45cd6ad0-2aa8-489a-a901-8e466dc138b3" />



## RESULT
The program for creating Image Carousel using React is executed successfully.
