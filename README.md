# SWAGVASTRA
An AI- fashion recommendations platform, it suggest the outfits based on the to ne of the body 

# Swag Vastra - AI-Powered Fashion Recommendation System

An intelligent fashion recommendation platform that uses computer vision and HSV color science to analyze skin tones and provide personalized outfit suggestions through an interactive multi-step wizard.

##  Features

### Core Functionality
- **AI Skin Tone Analysis**: MediaPipe Face Mesh + K-Means clustering for accurate tone detection (1-10 scale)
- **Multi-Step Wizard**: Guided journey from photo upload to personalized recommendations
- **Smart Color Matching**: Select primary color, then discover perfect matching combinations
- **Occasion-Based Styling**: Recommendations for Wedding, Formal, Casual, Party, Interview, Traditional, Date Night, and Sports
- **Gender-Specific Products**: Filtered recommendations for Male, Female, and Unisex preferences
- **HSV Color Science**: Scientific color matching based on Hue, Saturation, and Value principles

### Product Features
- Direct purchase links to mid and high-range brands
- Detailed product information (cloth type, price range, sizes)
- Occasion-specific accessory recommendations
- Price range filtering
- Product ratings and reviews
- Brand information

### User Experience
- Modern, responsive UI with smooth animations
- Step-by-step progress tracking
- Visual color selection with swatches
- Real-time loading states
- Mobile-friendly design

##  How It Works

### Step 1: Upload Photo
Upload a clear face photo for AI analysis

### Step 2: Choose Primary Color
Select your favorite color from AI-recommended suitable colors based on your skin tone

### Step 3: Choose Matching Color
Pick a complementary color that pairs perfectly with your primary choice

### Step 4: Select Occasion
Choose where you're heading (Wedding, Party, Casual, etc.)

### Step 5: Select Gender
Pick your style preference (Male, Female, or Unisex)

### Step 6: Get Recommendations
Browse personalized clothing and accessories with direct purchase links!

## 🛠️ Tech Stack

### Frontend
- Next.js 14 (App Router)
- TypeScript
- Tailwind CSS
- Framer Motion
- Lucide React Icons

### Backend
- Node.js + Express
- MongoDB + Mongoose
- Multer (file uploads)
- Axios

### AI Microservice
- Python 3.8+
- OpenCV
- MediaPipe
- Scikit-learn
- Flask

##  Installation

### Prerequisites
- Node.js 18+
- Python 3.8+
- MongoDB

### Quick Start

1. **Clone the repository**
```bash
git clone <repository-url>
cd swag-vastra
```

2. **Install AI Service**
```bash
cd ai-service
pip install -r requirements.txt
python app.py
```
Runs on `http://localhost:5000`

3. **Install Backend**
```bash
cd backend
npm install
cp .env.example .env
# Edit .env with your MongoDB URI
npm run seed  # Seed database with products
npm run dev
```
Runs on `http://localhost:3001`

4. **Install Frontend**
```bash
cd frontend
npm install
npm run dev
```
Runs on `http://localhost:3000`

### Detailed Setup
See [ENHANCED_SETUP_GUIDE.md](./ENHANCED_SETUP_GUIDE.md) for complete installation instructions.

### Quick Start All Services
See [START_ALL_SERVICES.md](./START_ALL_SERVICES.md) for running all services at once.

## Documentation

- **[ENHANCED_SETUP_GUIDE.md](./ENHANCED_SETUP_GUIDE.md)** - Complete setup and configuration guide
- **[START_ALL_SERVICES.md](./START_ALL_SERVICES.md)** - Quick start guide for all services
- **[CHANGES_SUMMARY.md](./CHANGES_SUMMARY.md)** - Detailed list of all enhancements
- **[IMPLEMENTATION_PLAN.md](./IMPLEMENTATION_PLAN.md)** - Technical implementation details
- **[PROJECT_STRUCTURE.md](./PROJECT_STRUCTURE.md)** - Project file structure
- **[SETUP_GUIDE.md](./SETUP_GUIDE.md)** - Original setup guide

##  Color Science

### HSV Analysis
- **Hue**: The actual color tone - identifies warm or cool undertones
- **Saturation**: Color intensity - determines vibrant or muted shades
- **Value**: Brightness level - measures light or dark tones

### Skin Tone Scale (1-10)
| Score | Label | Suitable Colors |
|-------|-------|----------------|
| 1-2 | Very Fair | Pastel Pink, Lavender, Mint Green, Peach, Light Blue, Cream |
| 3-4 | Fair | Coral, Turquoise, Rose, Powder Blue, Soft Yellow, Lilac |
| 5-6 | Medium | White, Sky Blue, Baby Pink, Orange, Emerald Green, Royal Blue |
| 7-8 | Dusky | Maroon, Mustard, Olive Green, Burnt Orange, Teal, Deep Purple |
| 9-10 | Deep | Bright Red, Electric Blue, Hot Pink, Lime Green, Gold, Magenta |

### Color Matching Examples
- **White** pairs with: Black, Navy Blue, Brown, Olive Green, Maroon
- **Baby Pink** pairs with: White, Gray, Navy Blue, Mint Green, Gold
- **Navy Blue** pairs with: White, Beige, Mustard, Coral, Light Gray

## 🔌 API Endpoints

### Wizard Flow
- `POST /api/wizard/start` - Start recommendation session
- `POST /api/wizard/select-primary-color` - Select primary color
- `POST /api/wizard/select-matching-color` - Select matching color
- `POST /api/wizard/select-occasion` - Select occasion
- `POST /api/wizard/select-gender` - Select gender
- `GET /api/wizard/recommendations/:sessionId` - Get final recommendations
- `GET /api/wizard/session/:sessionId` - Get session state

### Upload & Analysis
- `POST /api/upload` - Upload image for skin tone analysis
- `GET /api/recommendations/:analysisId` - Get recommendations

### AI Service
- `POST /analyze` - Analyze skin tone from image
- `GET /health` - Health check

## 🗂️ Project Structure

```
swag-vastra/
├── frontend/           # Next.js application
│   ├── app/
│   │   ├── page.tsx           # Landing page
│   │   ├── upload/            # Photo upload
│   │   ├── wizard/            # Multi-step wizard
│   │   └── recommendations/   # Final results
│   └── components/
│       └── wizard/            # Wizard step components
├── backend/            # Express API gateway
│   ├── src/
│   │   ├── routes/
│   │   │   ├── wizard.js      # Wizard endpoints
│   │   │   ├── upload.js
│   │   │   └── recommendations.js
│   │   ├── models/
│   │   │   ├── RecommendationSession.js
│   │   │   ├── Product.js
│   │   │   └── SkinAnalysis.js
│   │   └── services/
│   │       ├── matchingColorEngine.js
│   │       ├── recommendationEngine.js
│   │       └── combinationExplorer.js
└── ai-service/         # Python CV microservice
    ├── tone_classifier.py
    └── app.py
```

##  Usage

1. Visit `http://localhost:3000`
2. Click "Get Started"
3. Upload a clear face photo
4. Follow the wizard:
   - Select your primary color
   - Choose a matching color
   - Pick your occasion
   - Select gender preference
5. Browse personalized recommendations
6. Click "Buy Now" to purchase items

##  Testing

### Test the Complete Flow
1. Upload a test photo (clear face, good lighting)
2. Verify skin tone analysis (should show 1-10 score)
3. Select colors through wizard
4. Check final recommendations appear
5. Verify filters work (price range)
6. Test "Buy Now" links

### Sample Test Data
- **Skin Tone**: 5/10 (Medium)
- **Primary Color**: Baby Pink
- **Matching Color**: White
- **Occasion**: Party
- **Gender**: Female

## Production Deployment

### Build Frontend
```bash
cd frontend
npm run build
npm start
```

### Run Backend
```bash
cd backend
NODE_ENV=production npm start
```

### Run AI Service
```bash
cd ai-service
gunicorn -w 4 -b 0.0.0.0:5000 app:app
```

##  Environment Variables

### Backend (.env)
```
PORT=3001
MONGODB_URI=mongodb://localhost:27017/swag-vastra
AI_SERVICE_URL=http://localhost:5000
NODE_ENV=development
```

##  Troubleshooting

### AI Service Not Running
```
Error: AI service is not running
Solution: Start Python service on port 5000
```

### MongoDB Connection Error
```
Error: MongoDB Connection Error
Solution: Check MONGODB_URI and ensure MongoDB is running
```

### No Products Found
```
Error: No products in recommendations
Solution: Run seed script: npm run seed
```

## Future Enhancements

- Google OAuth authentication
- User profiles and saved recommendations
- Virtual try-on feature
- Social sharing
- Wishlist functionality
- Purchase history
- Style quiz
- Seasonal recommendations

## Contributing

1. Fork the repository
2. Create feature branch
3. Commit changes
4. Push to branch
5. Open pull request

##  License

MIT License

##  Credits

- MediaPipe by Google
- Color science research
- Fashion industry best practices

##  Support

For issues or questions:
1. Check documentation files
2. Review error messages
3. Ensure all services are running
4. Check MongoDB connection

---

**Made with  for fashion enthusiasts**

Visit the app at `http://localhost:3000` and discover your perfect style! 🎨👗✨

