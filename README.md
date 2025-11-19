# Image Processor – Frontend

A modern, responsive React application that allows users to upload images, apply real-time transformations, preview results, and download the processed image.  
Communicates with a Node.js + Sharp backend to perform processing operations.

---

## Features

- Upload images (JPG, PNG, JPEG)
- Choose processing operations:

  - Grayscale
  - Rotate (custom degrees)
  - Blur
  - Sharpen

- Adjustable sliders for intensity/rotation
- Live **Before / After** preview layout
- Automatic processing with debounce
- Download final processed image
- Custom CSS design using CSS variables
- Responsive layout with clean UI

---

## 🛠 Tech Stack

### **Frontend**

- React (Functional Components)
- React Hooks (useState, useEffect)
- Custom CSS3 using variables
- File handling with `Blob`, `ObjectURL`
- Axios for API calls
- Material Symbols (Google Icons)

### **Communication**

- Axios POST requests with **ArrayBuffer**
- Receives binary image response from backend

---

## 📦 Installation

Clone the repository:

`git clone https://github.com/therealakash13/image_processor_frontend.git cd frontend`

Install dependencies:

`npm install`

Start development server:

`npm run dev`

---

## Folder Structure

    frontend/
    ├── src/
    │   ├── components/
    │   │   └── Form.jsx
    │   ├── App.jsx
    │   ├── main.jsx
    │   └── styles.css
    ├── public/
    ├── package.json
    └── README.md

---

## Backend Connection

The frontend sends the image as ArrayBuffer:

    const response = await axios.post(
        `http://localhost:3000/upload?op=${operation}&level=${level}`, imageBuffer,
          { headers: { "Content-Type": "application/octet-stream" },
    	    responseType: "arraybuffer",
          }
    );

And receives the processed image as a Blob:

    const blob = new  Blob([response.data], { type: "image/png" });
    const url = URL.createObjectURL(blob);
    setProcessedImageUrl(url);

---

## Before / After Preview

The UI shows:

- Original upload
- Processed version
- Side-by-side layout
- Responsive for mobile screens

Clean and intuitive design.

---

## Downloading Processed Image

A download button triggers:

    const link = document.createElement("a");
    link.href = processedImageUrl;
    link.download = "processed-image.png";
    link.click();

---

## 🧪 Future Improvements

- Drag-and-drop upload
- Before/After slider
- Undo/Redo editing
- More processing effects (brightness, hue, saturation)
- Multi-step editing pipeline
- Dark/Light theme toggle
- Progress indicators and loaders
- Support for JPG/WEBP format selection

---
