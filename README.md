# 🎭 Agentic Image Personality

**Agentic Image Personality** is an AI-powered FastAPI application that analyzes uploaded images and generates personalized, culturally-aware responses. The project leverages Google Gemini AI models for vision analysis and creates engaging interactions based on dynamic AI personality profiles.

---

## ✨ Features

- **🔍 Advanced Image Analysis:** Uses Google Gemini vision models to describe and interpret uploaded images with cultural awareness
- **🎨 Dynamic AI Personalities:** Multiple customizable AI agents with unique voices and cultural perspectives
- **🌍 Cultural Intelligence:** AI recognizes and comments on cultural elements, adapting tone and language accordingly
- **📡 Production-Ready API:** FastAPI backend with comprehensive endpoints and automatic documentation
- **📓 Interactive Development:** Jupyter Notebook for experimentation and testing
- **☁️ Cloud Deployment:** Automated Google Cloud Run deployment via GitHub Actions
- **🔒 Secure Configuration:** Environment-based API key management

---

## 🎯 How It Works

1. **Upload an image** (e.g., selfie or portrait)
2. **AI analyzes the image** using Google Gemini vision models
3. **Cultural context recognition** identifies elements and background
4. **Personalized response generation** creates engaging, witty responses
5. **Culturally-aware delivery** adapts tone and language appropriately

---

## 🚀 Quick Start

### Prerequisites

- Python 3.9+
- Google Generative AI API key (Gemini)
- (Optional) Jupyter Notebook for interactive use

### 1. Clone & Setup
```bash
git clone https://github.com/yourusername/Agentic-ImagePersonality-3.git
cd Agentic-ImagePersonality-3
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### 2. Configure Environment
Create a `.env` file:
```env
GOOGLE_API_KEY=your_gemini_api_key_here
```

### 3. Run the API
```bash
python main.py
```
Visit `http://localhost:8000/docs` for the interactive API documentation.

---

## 📋 API Endpoints

### Core Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/` | API information and available personalities |
| `GET` | `/bots` | List all available AI agents |
| `POST` | `/analyze_image_with_file` | Upload image file for analysis |
| `POST` | `/analyze_image_with_base64` | Send base64 image for analysis |
| `GET` | `/health` | Health check and system status |

### Example Usage

#### Upload Image File
```bash
curl -X POST "http://localhost:8000/analyze_image_with_file" \
     -H "Content-Type: multipart/form-data" \
     -F "image=@your_image.jpg" \
     -F "bot_id=mentor_male"
```

#### Send Base64 Image
```bash
curl -X POST "http://localhost:8000/analyze_image_with_base64" \
     -H "Content-Type: application/json" \
     -d '{
       "image_base64": "iVBORw0KGgoAAAANSUhEUgAA...",
       "bot_id": "cultural_advisor"
     }'
```

---

## 🏗️ Project Structure

```
Agentic-ImagePersonality-3/
├── main.py                 # FastAPI application
├── bot_persona.py          # AI personality configurations
├── agenticImagePersonality1.ipynb  # Jupyter notebook for testing
├── requirements.txt        # Python dependencies
├── .env                    # Environment variables (create this)
├── .gitignore             # Git ignore rules
├── .github/
│   └── workflows/
│       └── deploy.yml     # GitHub Actions deployment
└── README.md              # This file
```

---

## 🔧 Development

### Interactive Development
Use the Jupyter notebook for experimentation:
```bash
jupyter notebook agenticImagePersonality1.ipynb
```

### Adding New AI Personalities
1. Edit [`bot_persona.py`](bot_persona.py)
2. Add your personality configuration
3. Test with the API endpoints

### Local Testing
```bash
# Start the server
python main.py

# Test health endpoint
curl http://localhost:8000/health

# Get available personalities
curl http://localhost:8000/bots
```

---

## ☁️ Deployment

### Google Cloud Run (Automated)
The project includes GitHub Actions for automatic deployment:

1. **Set up secrets in your GitHub repository:**
   - `GCP_CREDENTIALS`: Your Google Cloud service account JSON
   - `GOOGLE_API_KEY`: Your Gemini API key

2. **Push to main branch:**
   ```bash
   git push origin main
   ```

3. **Monitor deployment:** Check the Actions tab in your GitHub repository

### Manual Deployment
```bash
# Deploy to Cloud Run
gcloud run deploy fastapi-image-personality \
  --source . \
  --region us-central1 \
  --set-env-vars GOOGLE_API_KEY=$GOOGLE_API_KEY
```

---

## 📦 Dependencies

- **FastAPI** - Modern web framework for APIs
- **Google Generative AI** - Gemini vision and text models
- **Pillow** - Image processing
- **Uvicorn** - ASGI server
- **Pydantic** - Data validation

See [`requirements.txt`](requirements.txt) for complete list.

---

## 🔒 Security & Privacy

- API keys are managed through environment variables
- Images are temporarily processed and can be stored as base64
- No persistent storage of user images by default
- CORS middleware configured for frontend integration

---

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Make your changes and add tests
4. Commit your changes: `git commit -m 'Add feature'`
5. Push to the branch: `git push origin feature-name`
6. Submit a pull request

---


## 🆘 Support

- **Issues:** Report bugs or request features via GitHub Issues
- **Documentation:** Visit `/docs` endpoint when running locally
- **API Reference:** Interactive docs at `/docs` and `/redoc`

---
