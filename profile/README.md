# Field Voice AI - Complete Project Documentation

A full-stack voice AI application for agricultural pest and crop management, providing real-time assistance to farmers through voice and text interactions.

## 🌾 Project Overview

Field Voice AI is an intelligent agricultural assistant that helps farmers identify pests, diseases, and provides treatment recommendations for their crops. The system combines voice recognition, natural language processing, and a comprehensive agricultural knowledge base to deliver instant, accurate advice.

**Live Platform**: [https://field-voice.balanceapp.co.za/](https://field-voice.balanceapp.co.za/)

## 🏗️ Architecture

The application consists of two main components:

### Backend (NestJS)
- **Location**: `/eleven/`
- **Framework**: NestJS (Node.js)
- **Database**: MySQL
- **Port**: 4000 (default)
- **Features**: REST API, WebSocket support, Authentication, AI Agent integration

### Frontend (Next.js)
- **Location**: `/voice-frontend/`
- **Framework**: Next.js 16 (React)
- **Port**: 3000 (default)
- **Features**: Real-time chat, Voice interaction, File upload, Conversation history

## 🛠️ Tech Stack

### Backend Technologies
- **Framework**: NestJS 11
- **Database**: MySQL with TypeORM
- **Authentication**: JWT with Passport
- **WebSockets**: Socket.IO
- **AI Integration**: OpenAI, Google GenAI, ElevenLabs
- **File Processing**: PDF parsing, Image handling
- **Search**: Elasticsearch integration

### Frontend Technologies
- **Framework**: Next.js 16, React 19
- **Styling**: Tailwind CSS 4
- **WebSockets**: Socket.IO Client
- **Voice**: ElevenLabs React SDK
- **Markdown**: React Markdown with syntax highlighting
- **State Management**: React Context API

## 📊 Agricultural Knowledge Base

The system has been trained on an extensive agricultural database:

### Crops Database (223 crops)
- **Vegetables**: Carrots, Broccoli, Cabbage, Lettuce, Spinach, Tomatoes, Peppers, Onions, Potatoes, Sweet Potatoes, Cucumbers, Pumpkins, and many more
- **Fruits**: Apples, Oranges, Lemons, Grapes, Mangoes, Bananas, Peaches, Pears, Plums, and various citrus fruits
- **Grains**: Maize, Wheat, Barley, Oats, Rice, Sorghum, and Triticale
- **Nuts**: Pecan Nuts, Macadamia Nuts, Cashew Nuts, Almonds, Walnuts, and more
- **Herbs & Spices**: Basil, Rosemary, Thyme, Sage, Parsley, Coriander, Mint, and various others
- **Legumes**: Beans, Peas, and various bean varieties
- **Other**: Cotton, Tobacco, Sugarcane, Sunflower, Canola, and many specialty crops

### Pests Database (192 pests)
- **Insects**: Aphids (multiple varieties), Mites (Red spider mite, Two-spotted spider mite, etc.), Thrips, Scale insects, Mealybugs, Ants, and various caterpillars
- **Diseases**: Fungal diseases (Powdery mildew, Downy mildew, Rust, Blight, etc.), Bacterial diseases (Bacterial spot, Bacterial blight), and various leaf spots
- **Nematodes**: Root-knot nematode, Dagger nematode, Ring nematode, and others
- **Weeds**: Broadleaf weeds, Grass weeds, Sedges, and Noxious weeds
- **Other Pests**: Leaf miners, Bollworms, Army worms, Cutworms, and various agricultural pests

### Crop-Pest Relationships (1,163 combinations)

The system has been trained on **1,163 unique crop-pest relationships**, enabling it to provide specific recommendations for various agricultural scenarios.

**Example Combinations**:
- **Tomato**: Early blight, Late blight, Anthracnose, Aphids, Bollworm, White fly, Bacterial spot, Mites, Leaf miners
- **Potato**: Early blight, Late blight, Downy mildew, Potato tuber moth, Bollworm, Cutworm, Fusarium, Dry rot, Common scab
- **Maize**: Stalk borer, Army worms, Bollworm, Black maize beetle, Aphids, Rust, Leaf spot, Cob smut, Downy mildew
- **Grapes**: Mealy bug, Downy mildew, Mites, Thrips, Anthracnose, Bollworm, Botrytis, Powdery mildew, Fruit Fly

## 🚀 Quick Start Guide

### Prerequisites

- Node.js (v18 or higher)
- MySQL database server
- npm, yarn, pnpm, or bun package manager
- Google Maps API Key (optional, for frontend features)

### Step 1: Backend Setup

1. Navigate to the backend directory:
   ```bash
   cd eleven/
   ```

2. Install dependencies:
   ```bash
   yarn install
   # or
   npm install
   ```

3. Create a `.env` file in the backend root:
   ```env
   DB_HOST=localhost
   DB_PORT=3306
   DB_USERNAME=root
   DB_PASSWORD=your_password
   DB_DATABASE=farm_voice_ai
   PORT=4000
   NODE_ENV=development
   ```

4. Ensure MySQL database `farm_voice_ai` exists:
   ```sql
   CREATE DATABASE farm_voice_ai;
   ```

5. Start the backend server:
   ```bash
   yarn dev
   # or
   npm run dev
   ```

   The backend will be available at `http://localhost:4000`

### Step 2: Frontend Setup

1. Navigate to the frontend directory:
   ```bash
   cd voice-frontend/
   ```

2. Install dependencies:
   ```bash
   yarn install
   # or
   npm install
   ```

3. Create a `.env.local` file in the frontend root:
   ```env
   NEXT_PUBLIC_GOOGLE_MAPS_API_KEY=your_google_maps_api_key_here
   ```

4. Start the frontend server:
   ```bash
   yarn dev
   # or
   npm run dev
   ```

   The frontend will be available at `http://localhost:3000`

### Step 3: Access the Application

1. Open your browser and navigate to: `http://localhost:3000`
2. You will be redirected to the login page
3. Use the test credentials:
   - **Email**: `dyorajackson@gmail.com`
   - **Password**: `123456`

## 🔐 Test Credentials

For testing and evaluation purposes:

- **Email**: `dyorajackson@gmail.com`
- **Password**: `123456`

## ✨ Key Features

### User Features
- **Real-time Chat**: WebSocket-based chat interface for instant AI responses
- **Voice Interaction**: Voice input and output capabilities using ElevenLabs
- **File Upload**: Upload and manage agricultural documents (PDFs, images)
- **Conversation History**: View and navigate past conversations
- **Authentication**: Secure login and session management
- **Responsive Design**: Works on desktop and mobile devices

### AI Capabilities
- **Pest Identification**: Identify pests and diseases from descriptions or images
- **Treatment Recommendations**: Get specific treatment advice for crop-pest combinations
- **Multi-language Support**: Natural language understanding for agricultural queries
- **Context Awareness**: Maintains conversation context for follow-up questions
- **Knowledge Base**: Access to 1,163 crop-pest relationships

## 📁 Project Structure

### Backend Structure (`eleven/`)
```
src/
├── entities/          # TypeORM database entities
│   ├── crop.entity.ts
│   ├── pest.entity.ts
│   ├── user.entity.ts
│   └── ...
├── logic/             # Business logic modules
│   ├── agent/        # AI agent logic
│   ├── auth/         # Authentication & authorization
│   ├── conversation/  # Conversation management
│   ├── elastic/      # Elasticsearch integration
│   ├── stt/          # Speech-to-text
│   └── web/          # Web services
├── prompts/          # AI prompts
└── utils/            # Utility functions
```

### Frontend Structure (`voice-frontend/`)
```
app/
├── (dashboard)/      # Protected dashboard routes
│   ├── chat/         # Chat interface
│   ├── history/      # Conversation history
│   ├── settings/      # User settings
│   └── policies/     # Policies page
├── login/            # Login page
└── layout.tsx        # Root layout

components/
├── VoiceChat.tsx     # Voice chat component
├── ChatMessages.tsx  # Chat messages display
├── FileUpload.tsx    # File upload component
└── ...

context/
├── AuthContext.tsx   # Authentication context
└── SocketContext.tsx # WebSocket context
```

## 🔧 Available Scripts

### Backend Scripts
```bash
yarn dev          # Start development server with watch
yarn build        # Build the project
yarn start        # Start production server
yarn start:prod   # Start production server from dist
yarn test         # Run unit tests
yarn test:e2e     # Run end-to-end tests
yarn lint         # Run ESLint
```

### Frontend Scripts
```bash
yarn dev          # Start development server
yarn build        # Build for production
yarn start        # Start production server
yarn lint         # Run ESLint
yarn pm2:start    # Start with PM2
yarn pm2:stop     # Stop PM2 process
yarn pm2:logs     # View PM2 logs
```

## 🌐 API Endpoints

### Authentication
- `POST /auth/login` - User login
- `POST /auth/register` - User registration
- `GET /auth/profile` - Get user profile

### Conversations
- `GET /conversations` - Get user conversations
- `POST /conversations` - Create new conversation
- `GET /conversations/:id` - Get conversation details
- `POST /conversations/:id/messages` - Send message

### WebSocket Events
- `message` - Send/receive chat messages
- `voice` - Voice input/output streaming
- `connection` - WebSocket connection management

## 🗄️ Database Schema

The application uses MySQL with the following main entities:

- **Users**: User accounts and authentication
- **Crops**: Crop database (223 crops)
- **Pests**: Pest database (192 pests)
- **Crop_Pests**: Relationship table (1,163 relationships)
- **Conversations**: User conversation history
- **Messages**: Individual messages in conversations
- **Chemicals**: Chemical/pesticide database
- **Crop_Chemicals**: Crop-chemical relationships

## 🔌 Environment Variables

### Backend (`.env`)
```env
DB_HOST=localhost
DB_PORT=3306
DB_USERNAME=root
DB_PASSWORD=your_password
DB_DATABASE=farm_voice_ai
PORT=4000
NODE_ENV=development
JWT_SECRET=your_jwt_secret
OPENAI_API_KEY=your_openai_key
GOOGLE_GENAI_API_KEY=your_google_genai_key
ELEVENLABS_API_KEY=your_elevenlabs_key
```

### Frontend (`.env.local`)
```env
NEXT_PUBLIC_GOOGLE_MAPS_API_KEY=your_google_maps_api_key
```

## 🚢 Deployment

### Production Build

**Backend**:
```bash
cd eleven/
yarn build
yarn start:prod
```

**Frontend**:
```bash
cd voice-frontend/
yarn build
yarn start
```

### PM2 Deployment (Frontend)

The frontend includes PM2 configuration for process management:

```bash
yarn pm2:start    # Start application
yarn pm2:stop     # Stop application
yarn pm2:restart  # Restart application
yarn pm2:logs     # View logs
```

## 🧪 Testing

### Backend Tests
```bash
cd eleven/
yarn test         # Unit tests
yarn test:e2e     # End-to-end tests
yarn test:cov     # Coverage report
```

## 🐛 Troubleshooting

### Common Issues

1. **Backend won't start**
   - Check MySQL is running
   - Verify database `farm_voice_ai` exists
   - Check `.env` file configuration
   - Ensure port 4000 is not in use

2. **Frontend can't connect to backend**
   - Verify backend is running on port 4000
   - Check `API_BASE_URL` in `types/contstants.ts`
   - Check CORS settings in backend

3. **WebSocket connection fails**
   - Ensure backend WebSocket gateway is configured
   - Check firewall settings
   - Verify Socket.IO adapter is properly set up

4. **Authentication errors**
   - Verify JWT secret is set in backend `.env`
   - Check token expiration settings
   - Clear browser localStorage and try again

## 📚 Additional Resources

- **Backend README**: See `eleven/README.md` for detailed backend documentation
- **Frontend README**: See `voice-frontend/README.md` for detailed frontend documentation
- **Judges Guide**: See `voice-frontend/JUDGES.md` for evaluation instructions

## 🤝 Contributing

When contributing to this project:

1. Follow the existing code style
2. Write tests for new features
3. Update documentation as needed
4. Ensure both backend and frontend work together

## 📄 License

See LICENSE files in respective project directories.

## 📞 Support

For issues or questions:
- Check the troubleshooting section above
- Review the individual README files for each project
- Check the Judges guide for testing instructions

---

**Built with ❤️ for farmers and agricultural professionals**

