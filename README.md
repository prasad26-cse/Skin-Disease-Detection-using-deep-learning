# Skin-Disease-Detection-using-deep-learning

A beautiful, responsive single-page web application for classifying skin lesions using deep learning. Upload an image and get instant AI-powered predictions with detailed probability analysis.

![Python](https://img.shields.io/badge/Python-3.11%2B-blue)
![Flask](https://img.shields.io/badge/Flask-3.0.0-green)
![TensorFlow](https://img.shields.io/badge/TensorFlow-CPU-orange)
![License](https://img.shields.io/badge/License-Educational-yellow)

## ✨ Features

- **🎨 Modern UI Design**: Beautiful gradient color combinations with smooth animations
- **📱 Fully Responsive**: Works seamlessly on desktop, tablet, and mobile devices
- **🖼️ Drag & Drop Upload**: Easy image upload with drag-and-drop support
- **⚠️ Smart Disclaimer**: Prominent warning to upload skin disease-related images only
- **🤖 AI-Powered**: Uses a trained deep learning model (final_model.h5) for classification
- **📊 Detailed Results**: Interactive table showing all classification probabilities
- **⚡ Real-time Analysis**: Instant predictions with confidence scores
- **💾 Download Results**: Export analysis results as a text file
- **🎭 Smooth Animations**: Engaging user experience with CSS animations and transitions
- **🌈 Color-Coded Rankings**: Visual indicators for top predictions

## 🎯 Supported Classifications

The model can classify the following **7 skin lesion types**:

1. **Actinic Keratosis** - Precancerous skin growth
2. **Basal Cell Carcinoma** - Most common type of skin cancer
3. **Benign Keratosis** - Non-cancerous skin growth
4. **Dermatofibroma** - Common benign skin nodule
5. **Melanoma** - Most serious type of skin cancer
6. **Melanocytic Nevus** - Common mole
7. **Vascular Lesion** - Blood vessel abnormality

## 🚀 Quick Start

### Prerequisites
- **Python 3.11 or 3.12** (recommended for TensorFlow compatibility)
- **pip** package manager
- **8GB RAM** minimum (for model loading)

### Installation Steps

1. **Navigate to the project directory**
   ```bash
   cd "c:\Users\VICTUS\OneDrive\Desktop\Skin"
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv .venv
   ```

3. **Activate the virtual environment**
   
   **Windows:**
   ```bash
   .venv\Scripts\activate
   ```
   
   **macOS/Linux:**
   ```bash
   source .venv/bin/activate
   ```

4. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```
   
   > **Note**: Installation may take 5-10 minutes due to TensorFlow download size.

5. **Verify model file exists**
   ```bash
   # Ensure final_model (2).h5 is in the project root
   ```

## 🎮 Usage

### Starting the Application

1. **Run the Flask server**
   ```bash
   python app.py
   ```

2. **Open your browser**
   
   Navigate to: **http://localhost:5000**

3. **Upload and Analyze**
   - Read the disclaimer notice
   - Click the upload area or drag & drop a skin lesion image
   - Review the image preview
   - Click **"Analyze Image"** button
   - View detailed results with confidence scores
   - Download results as a text file (optional)

### Expected Workflow

```
Upload Image → Preview → Analyze → View Results → Download (Optional) → New Analysis
```

## 📁 Project Structure

```
Skin/
├── app.py                      # Flask backend API with ML model integration
├── final_model (2).h5          # Trained deep learning model (35MB)
├── requirements.txt            # Python dependencies
├── README.md                   # Project documentation (this file)
├── .venv/                      # Virtual environment (created after setup)
├── templates/
│   └── index.html             # Main HTML template with all sections
└── static/
    ├── style.css              # CSS styling with animations & gradients
    └── script.js              # JavaScript for interactivity & API calls
```

## 🎨 Design & UI

### Color Scheme
The application uses a **modern dark theme** with vibrant gradient accents:

| Element | Colors |
|---------|--------|
| **Primary** | Purple-Blue gradient (#667eea → #764ba2) |
| **Secondary** | Pink gradient (#f093fb → #f5576c) |
| **Accent** | Cyan gradient (#4facfe → #00f2fe) |
| **Success** | Green gradient (#43e97b → #38f9d7) |
| **Warning** | Orange (#f59e0b) |
| **Background** | Dark slate (#0f172a, #1e293b) |

### Key UI Components

- **Animated Background**: Floating gradient circles
- **Hero Section**: Stats cards with hover effects
- **Disclaimer Notice**: Prominent warning with animated icon
- **Upload Area**: Drag & drop with visual feedback
- **Results Table**: Responsive table with color-coded rankings
- **Confidence Meter**: Animated progress bar
- **Smooth Scrolling**: Navigation between sections

## 🔧 Technical Stack

| Category | Technology |
|----------|-----------|
| **Backend** | Flask 3.0.0 |
| **Frontend** | HTML5, CSS3, Vanilla JavaScript |
| **ML Framework** | TensorFlow-CPU, Keras |
| **Image Processing** | Pillow (PIL) |
| **Icons** | Font Awesome 6.4.0 |
| **Fonts** | Google Fonts (Poppins) |
| **API** | REST API (JSON) |

## 📱 Responsive Design

The application is fully responsive with breakpoints:

- **Desktop**: 1200px and above - Full layout with all features
- **Tablet**: 768px - 1199px - Optimized grid layout
- **Mobile**: Below 768px - Single column, touch-friendly

## 🔌 API Endpoints

### `POST /predict`
Analyzes uploaded image and returns predictions.

**Request:**
- Method: `POST`
- Content-Type: `multipart/form-data`
- Body: `image` file

**Response:**
```json
{
  "success": true,
  "prediction": "Melanoma",
  "confidence": 87.45,
  "all_results": [
    {
      "class": "Melanoma",
      "probability": 0.8745,
      "percentage": 87.45
    },
    ...
  ]
}
```

### `GET /health`
Health check endpoint.

**Response:**
```json
{
  "status": "healthy",
  "model_loaded": true
}
```

## ⚠️ Important Disclaimer

**⚠️ MEDICAL DISCLAIMER**

This tool is for **educational and research purposes ONLY**. It is NOT a medical device and should NEVER be used as a substitute for professional medical advice, diagnosis, or treatment.

- ❌ Do NOT use for self-diagnosis
- ❌ Do NOT delay seeking medical care based on results
- ✅ Always consult a qualified dermatologist or healthcare professional
- ✅ Use only skin lesion/disease-related images for accurate results

## 🛠️ Customization Guide

### 1. Changing Model Classes

Edit the `CLASS_NAMES` list in `app.py`:

```python
CLASS_NAMES = [
    'Your Class 1',
    'Your Class 2',
    'Your Class 3',
    # ... add your classes
]
```

### 2. Adjusting Image Preprocessing

Modify the `preprocess_image` function in `app.py`:

```python
def preprocess_image(image, target_size=(224, 224)):
    # Adjust target_size based on your model's input shape
    # Modify normalization if needed
```

### 3. Customizing Colors

Edit CSS variables in `static/style.css`:

```css
:root {
    --primary-color: #your-color;
    --gradient-1: linear-gradient(135deg, #color1, #color2);
    /* ... modify other variables */
}
```

### 4. Changing Port

Edit `app.py`:

```python
if __name__ == '__main__':
    app.run(debug=True, host='0.0.0.0', port=5001)  # Change port
```

## 🐛 Troubleshooting

### Issue: TensorFlow Installation Fails

**Solution:**
- Use Python 3.11 or 3.12 (Python 3.13 has limited TensorFlow support)
- Try installing `tensorflow-cpu` instead of `tensorflow`
- On Windows, ensure Microsoft Visual C++ Redistributable is installed

### Issue: Model Not Loading

**Solution:**
- Verify `final_model (2).h5` exists in the project root
- Check file is not corrupted (should be ~35MB)
- Ensure TensorFlow/Keras is properly installed
- Check console logs for specific error messages

### Issue: Port Already in Use

**Solution:**
```bash
# Find process using port 5000
netstat -ano | findstr :5000

# Kill the process or change port in app.py
```

### Issue: Image Upload Not Working

**Solution:**
- Ensure image is JPG, PNG, or JPEG format
- Check file size (very large images may timeout)
- Verify browser supports File API (use modern browsers)
- Check browser console for JavaScript errors

### Issue: Slow Predictions

**Solution:**
- First prediction is slower (model loading)
- Subsequent predictions should be faster
- Consider using GPU version of TensorFlow for faster inference
- Reduce image size before upload

## 📊 Performance

- **Model Size**: ~35MB
- **First Prediction**: 3-5 seconds (includes model loading)
- **Subsequent Predictions**: 1-2 seconds
- **Supported Image Formats**: JPG, PNG, JPEG
- **Recommended Image Size**: 224x224 to 1024x1024 pixels

## 🔒 Security Notes

- Model runs locally (no data sent to external servers)
- Images are processed in memory (not saved to disk)
- CORS enabled for local development
- For production: Add authentication, HTTPS, rate limiting

## 📝 Future Enhancements

- [ ] Add image preprocessing options (brightness, contrast)
- [ ] Support batch image upload
- [ ] Add confidence threshold settings
- [ ] Export results as PDF
- [ ] Add image augmentation preview
- [ ] Multi-language support
- [ ] Dark/Light theme toggle
- [ ] Model performance metrics display

## 📄 License

This project is provided **as-is for educational purposes**. 

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Fork the repository
- Create feature branches
- Submit pull requests
- Report bugs or issues
- Suggest enhancements

## 👨‍💻 Development

Built with modern web technologies and best practices:
- Clean, modular code structure
- Responsive design principles
- Accessibility considerations
- Cross-browser compatibility
- Performance optimizations

## 📞 Support

For issues or questions:
1. Check the Troubleshooting section
2. Review console logs for errors
3. Verify all dependencies are installed
4. Ensure Python version compatibility

---

**Made with ❤️ using AI & Machine Learning**

*Last Updated: October 2025*
