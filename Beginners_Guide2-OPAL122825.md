Complete Guide: Using OPAL Specification Skills for Application Generation
Table of Contents

Introduction
Understanding the SKILL.md
Platform-Specific Instructions
5 Detailed Step-by-Step Examples
Troubleshooting & Tips


Introduction
What is OPAL?
OPAL (Optimized Programming and Application Logic) is an AI-powered code generation system that can create complete applications from detailed technical specifications. The SKILL.md document provides instructions that help AI systems like Claude generate comprehensive technical specifications.
What You'll Learn

How to use the SKILL.md prompt effectively
How to generate technical specifications for applications
How to feed those specifications to OPAL for application generation
5 real-world examples with complete workflows

Prerequisites

Access to Claude.ai (Free or Pro account)
OR access to ChatGPT Plus/Enterprise
OR API access to any LLM
Basic understanding of software applications
Text editor (VS Code, Notepad++, or any text editor)


Understanding the SKILL.md
What Does SKILL.md Do?
The SKILL.md document is a meta-prompt that instructs an AI to:

Analyze code or application descriptions
Generate comprehensive technical specifications
Structure the output in a format OPAL can understand
Include all necessary details for complete application generation

Key Components of SKILL.md
Copy┌─────────────────────────────────────────┐
│         SKILL.md Structure              │
├─────────────────────────────────────────┤
│ 1. Analysis Instructions                │
│    - What to identify                   │
│    - What to document                   │
│                                         │
│ 2. Required Specification Sections      │
│    - Executive Summary                  │
│    - Technology Stack                   │
│    - Data Models                        │
│    - UI/UX & Theming                    │
│    - Component Specifications           │
│    - Service Layer                      │
│    - Security & Configuration           │
│    - Dependencies                       │
│                                         │
│ 3. Formatting Requirements              │
│    - Markdown structure                 │
│    - Code blocks                        │
│    - Detail level                       │
└─────────────────────────────────────────┘

Platform-Specific Instructions
Option 1: Using Claude.ai Console (Recommended for Beginners)
Setup Steps:

Access Claude

Go to https://claude.ai
Sign in or create an account
Start a new conversation


Prepare Your Workspace

Open a text editor (Notepad, VS Code, etc.)
Keep Claude in one window, text editor in another


Basic Workflow
CopyStep 1: Paste SKILL.md into Claude
Step 2: Add your application description/code
Step 3: Claude generates specification
Step 4: Copy specification to text editor
Step 5: Save as .md file
Step 6: Use with OPAL


Character Limits:

Claude Sonnet: ~200K characters input
Claude Opus: ~200K characters input
Strategy: If your code is too long, break it into sections


Option 2: Using ChatGPT
Setup Steps:

Access ChatGPT

Go to https://chat.openai.com
Sign in (requires Plus or Enterprise for best results)
Start new chat


Workflow Differences

ChatGPT has smaller context window than Claude
May need to break SKILL.md into smaller parts
Use GPT-4 for best results


Best Practices
Copy- Use Custom Instructions feature to store SKILL.md
- Break large code into sections
- Ask for specific sections one at a time



Option 3: Using API (Advanced)
Python Example:
pythonCopyimport anthropic
import os

def generate_specification(skill_content, app_description):
    client = anthropic.Anthropic(api_key=os.environ.get("ANTHROPIC_API_KEY"))
    
    prompt = f"""{skill_content}

<app_description>
{app_description}
</app_description>

<code_or_spec>
# No code provided, generate from description
</code_or_spec>
"""
    
    message = client.messages.create(
        model="claude-3-5-sonnet-20241022",
        max_tokens=16000,
        messages=[
            {"role": "user", "content": prompt}
        ]
    )
    
    return message.content[0].text

# Usage
with open('SKILL.md', 'r') as f:
    skill_content = f.read()

app_description = """
Create a task management application with:
- User authentication
- Project creation
- Task assignment
- Due date tracking
- Email notifications
"""

specification = generate_specification(skill_content, app_description)

with open('task_app_spec.md', 'w') as f:
    f.write(specification)

5 Detailed Step-by-Step Examples

Example 1: Simple Todo List Application
📋 Scenario
You want to create a basic todo list web application and need OPAL to generate it.
🎯 Goal
Generate a complete technical specification for a todo list app that OPAL can use.
📝 Step-by-Step Instructions
STEP 1: Prepare Your Application Description
Open your text editor and write:
markdownCopy# Todo List Application Description

I want to create a simple todo list web application with these features:

1. **User Interface**:
   - Clean, modern design
   - Single page application
   - Responsive (works on mobile and desktop)

2. **Features**:
   - Add new tasks with a text input
   - Mark tasks as complete (checkbox)
   - Delete tasks
   - Filter tasks (All, Active, Completed)
   - Task counter showing remaining tasks
   - Local storage to persist tasks

3. **Technology Preferences**:
   - Pure HTML, CSS, JavaScript (no frameworks)
   - Modern CSS (Flexbox/Grid)
   - Clean, maintainable code

4. **Design**:
   - Minimalist design
   - Blue and white color scheme
   - Smooth animations
   - Clear visual feedback
Save this as todo_description.txt

STEP 2: Open Claude.ai

Go to https://claude.ai
Click "Start new chat"
You should see an empty conversation


STEP 3: Paste the SKILL.md Content
Copy the entire SKILL.md document and paste it into Claude. It starts with:
CopyYou will be analyzing code or technical specifications and generating comprehensive instructions...
What to expect: Claude will acknowledge receiving the instructions (usually says "I understand" or similar).

STEP 4: Add Your Application Description
In the same message (or immediately after), add:
CopyNow, please generate a comprehensive technical specification for the following application:

<app_description>
[PASTE YOUR TODO_DESCRIPTION.TXT CONTENT HERE]
</app_description>

<code_or_spec>
# No existing code - generate specification from description
</code_or_spec>

STEP 5: Submit and Wait

Click Send or press Enter
Claude will take 30-60 seconds to generate the specification
The output will be 10-20 pages of detailed technical specifications


STEP 6: Review the Generated Specification
Claude will generate something like:
markdownCopy<specification>

# Technical Specification: Todo List Application

## 1. Executive Summary

### 1.1 Application Overview
A single-page todo list application built with vanilla JavaScript...

### 1.2 Core Functionality
- Task management (Create, Read, Update, Delete)
- Task filtering and status management
- Persistent storage using localStorage
- Responsive design for all devices

[... continues for many pages ...]

## 2. Technology Stack

### 2.1 Core Technologies
- **HTML5**: Semantic markup, modern APIs
- **CSS3**: Flexbox, Grid, Custom Properties, Animations
- **JavaScript ES6+**: Modules, Classes, Local Storage API

[... continues ...]

## 3. Data Models

```javascript
class Task {
    constructor(id, text, completed = false, createdAt = new Date()) {
        this.id = id;
        this.text = text;
        this.completed = completed;
        this.createdAt = createdAt;
    }
}
[... continues ...]
Copy
---

#### **STEP 7: Copy the Specification**

1. Scroll to the top of Claude's response
2. Look for the opening `<specification>` tag
3. Select everything from `<specification>` to `</specification>`
4. Copy to clipboard (Ctrl+C or Cmd+C)

---

#### **STEP 8: Save the Specification**

1. Open your text editor
2. Create a new file
3. Paste the specification
4. Save as `todo_app_specification.md`

**File structure:**
my-project/
├── todo_description.txt          # Your original idea
└── todo_app_specification.md     # Generated specification
Copy
---

#### **STEP 9: Use with OPAL**

Now you can feed this specification to OPAL:

**If using OPAL via Claude/ChatGPT:**
I have a detailed technical specification for an application.
Please generate the complete code based on this specification:
[PASTE todo_app_specification.md CONTENT]
Please generate:

index.html
styles.css
app.js
README.md with setup instructions

Copy
**If using OPAL API/Platform:**

Upload the `todo_app_specification.md` file to the OPAL platform and click "Generate Application".

---

#### **STEP 10: Iterate if Needed**

If you want to modify something:

**Go back to Claude and say:**
Please update the specification to add these features:

Dark mode toggle
Task priority levels (High, Medium, Low)
Due dates for tasks

Update sections 3 (Data Models), 5 (Component Specifications),
and 4 (UI/UX) accordingly.
Copy
---

### ✅ Expected Results

You should now have:
- ✓ A 15-20 page technical specification
- ✓ Complete data models in code
- ✓ Detailed UI/UX specifications
- ✓ Component breakdowns
- ✓ CSS styling details
- ✓ Ready to feed to OPAL

---

## Example 2: Recipe Manager App with Database

### 📋 Scenario
You want to create a recipe management application with a backend database, and you have some rough code ideas.

### 🎯 Goal
Generate a comprehensive specification including frontend, backend, and database design.

### 📝 Step-by-Step Instructions

#### **STEP 1: Prepare Your Input Materials**

Create a file called `recipe_app_concept.md`:

```markdown
# Recipe Manager Application

## Overview
A web application for managing personal recipes with search, categories, and shopping lists.

## Features Required

### User Management
- User registration and login
- Profile with favorite recipes
- Recipe sharing between users

### Recipe Management
- Create/edit/delete recipes
- Recipe fields:
  - Title
  - Description
  - Ingredients (with quantities)
  - Instructions (step-by-step)
  - Prep time / Cook time
  - Servings
  - Difficulty level
  - Categories/Tags
  - Photos
- Rich text editor for instructions
- Ingredient scaling (adjust servings)

### Organization
- Categories (Breakfast, Lunch, Dinner, Desserts, etc.)
- Tags (Vegetarian, Gluten-Free, Quick, etc.)
- Search functionality (by name, ingredient, tag)
- Filter by prep time, difficulty
- Favorites/bookmarking

### Shopping List
- Add recipe ingredients to shopping list
- Combine ingredients from multiple recipes
- Check off items
- Export/print shopping list

### Additional Features
- Recipe ratings and reviews
- Nutritional information (optional)
- Print-friendly recipe view
- Recipe import from URL
- Mobile responsive

## Technical Requirements

### Frontend
- Modern React application
- TypeScript for type safety
- Material-UI for components
- Responsive design
- Image upload and optimization

### Backend
- Node.js with Express
- RESTful API
- JWT authentication
- PostgreSQL database
- Image storage (local or cloud)

### Deployment
- Docker containerization
- Environment-based configuration
- Ready for cloud deployment (AWS/GCP/Azure)

STEP 2: Create Sample Code Snippets (Optional)
If you have some code ideas, create sample_code.js:
javascriptCopy// Sample data model idea
const Recipe = {
  id: 'uuid',
  userId: 'uuid',
  title: 'string',
  description: 'string',
  ingredients: [
    {
      name: 'string',
      quantity: 'number',
      unit: 'string',
      notes: 'string'
    }
  ],
  instructions: [
    {
      stepNumber: 'number',
      instruction: 'string',
      imageUrl: 'string (optional)'
    }
  ],
  prepTime: 'number (minutes)',
  cookTime: 'number (minutes)',
  servings: 'number',
  difficulty: 'easy|medium|hard',
  categories: ['array of strings'],
  tags: ['array of strings'],
  imageUrl: 'string',
  createdAt: 'timestamp',
  updatedAt: 'timestamp'
};

// Sample API endpoint idea
app.post('/api/recipes', authenticateToken, async (req, res) => {
  // Create new recipe
});

app.get('/api/recipes/search', async (req, res) => {
  // Search recipes by query, filters
});

STEP 3: Open Claude and Paste SKILL.md

Go to claude.ai
Start new conversation
Paste the entire SKILL.md document
Wait for acknowledgment


STEP 4: Provide Your Application Materials
Continue in the same conversation:
CopyNow please generate a comprehensive technical specification for this application:

<app_description>
[PASTE CONTENT FROM recipe_app_concept.md]
</app_description>

<code_or_spec>
[PASTE CONTENT FROM sample_code.js]

Note: This is preliminary code structure. Please expand and formalize it 
in the specification with complete type definitions, API contracts, 
database schemas, and component hierarchies.
</code_or_spec>

STEP 5: Submit and Monitor

Click Send
This will take 60-90 seconds due to complexity
Claude will generate 30-50 pages of specification


STEP 6: Review the Output Structure
The specification will include:
markdownCopy<specification>

# Technical Specification: Recipe Manager Application

## 1. Executive Summary
[Overview of the application]

## 2. Technology Stack
### 2.1 Frontend Stack
- React 18.2+
- TypeScript 5.0+
- Material-UI 5.14+
- React Router 6.x
- React Query for data fetching
- Formik + Yup for forms
- Axios for HTTP requests

### 2.2 Backend Stack
- Node.js 18 LTS
- Express 4.18+
- TypeScript
- PostgreSQL 15+
- Prisma ORM
- JWT for authentication
- Multer for file uploads
- Sharp for image processing

### 2.3 DevOps & Deployment
- Docker & Docker Compose
- Nginx as reverse proxy
- PM2 for process management
- PostgreSQL in container

## 3. Data Models

### 3.1 Database Schema (Prisma)

```prisma
model User {
  id            String    @id @default(uuid())
  email         String    @unique
  passwordHash  String
  firstName     String
  lastName      String
  avatarUrl     String?
  createdAt     DateTime  @default(now())
  updatedAt     DateTime  @updatedAt
  
  recipes       Recipe[]
  favorites     FavoriteRecipe[]
  ratings       RecipeRating[]
  shoppingLists ShoppingList[]
}

model Recipe {
  id            String    @id @default(uuid())
  userId        String
  user          User      @relation(fields: [userId], references: [id])
  
  title         String
  description   String
  imageUrl      String?
  prepTime      Int       // minutes
  cookTime      Int       // minutes
  servings      Int
  difficulty    Difficulty
  
  ingredients   Ingredient[]
  instructions  Instruction[]
  categories    RecipeCategory[]
  tags          RecipeTag[]
  
  ratings       RecipeRating[]
  favorites     FavoriteRecipe[]
  
  createdAt     DateTime  @default(now())
  updatedAt     DateTime  @updatedAt
  
  @@index([userId])
  @@index([title])
}

model Ingredient {
  id         String  @id @default(uuid())
  recipeId   String
  recipe     Recipe  @relation(fields: [recipeId], references: [id], onDelete: Cascade)
  
  name       String
  quantity   Float
  unit       String
  notes      String?
  order      Int
  
  @@index([recipeId])
}

[... continues with all models ...]
3.2 TypeScript Interfaces
typescriptCopy// Frontend type definitions
interface Recipe {
  id: string;
  userId: string;
  title: string;
  description: string;
  imageUrl?: string;
  prepTime: number;
  cookTime: number;
  servings: number;
  difficulty: 'easy' | 'medium' | 'hard';
  ingredients: Ingredient[];
  instructions: Instruction[];
  categories: Category[];
  tags: Tag[];
  averageRating?: number;
  totalRatings?: number;
  isFavorite?: boolean;
  createdAt: string;
  updatedAt: string;
}

[... continues ...]
4. UI/UX & Theming
4.1 Design System
[Detailed color palette, typography, spacing]
4.2 Component Hierarchy
[Complete component tree]
5. Component Specifications
5.1 Frontend Components
5.1.1 RecipeCard Component
typescriptCopyinterface RecipeCardProps {
  recipe: Recipe;
  onFavoriteToggle: (recipeId: string) => void;
  onView: (recipeId: string) => void;
}

export const RecipeCard: React.FC<RecipeCardProps> = ({ 
  recipe, 
  onFavoriteToggle, 
  onView 
}) => {
  // Implementation details
  [... complete component code ...]
}
[... continues for 20+ components ...]
6. Service Layer
6.1 API Endpoints
Recipe Endpoints
typescriptCopy// POST /api/recipes
// Create new recipe
Request Body:
{
  title: string;
  description: string;
  prepTime: number;
  cookTime: number;
  servings: number;
  difficulty: 'easy' | 'medium' | 'hard';
  ingredients: Array<{
    name: string;
    quantity: number;
    unit: string;
    notes?: string;
  }>;
  instructions: Array<{
    stepNumber: number;
    instruction: string;
  }>;
  categories: string[];
  tags: string[];
}

Response: 201 Created
{
  id: string;
  ...recipe data
}

// GET /api/recipes/search
Query Parameters:
  - q: string (search query)
  - category: string[]
  - tags: string[]
  - difficulty: 'easy' | 'medium' | 'hard'
  - maxPrepTime: number
  - page: number
  - limit: number

Response: 200 OK
{
  recipes: Recipe[];
  total: number;
  page: number;
  totalPages: number;
}

[... all API endpoints with full specifications ...]
6.2 Backend Services
typescriptCopy// RecipeService.ts
class RecipeService {
  constructor(private prisma: PrismaClient) {}
  
  async createRecipe(userId: string, data: CreateRecipeDTO): Promise<Recipe> {
    // Implementation with error handling
    [... complete implementation ...]
  }
  
  async searchRecipes(filters: RecipeSearchFilters): Promise<PaginatedRecipes> {
    // Implementation with filtering, pagination
    [... complete implementation ...]
  }
  
  [... all service methods ...]
}
7. Security & Configuration
7.1 Authentication Flow
[Detailed JWT implementation]
7.2 Environment Variables
bashCopy# Backend .env
DATABASE_URL=postgresql://user:password@localhost:5432/recipedb
JWT_SECRET=your-secret-key
JWT_EXPIRATION=7d
PORT=5000
NODE_ENV=development
UPLOAD_DIR=./uploads
MAX_FILE_SIZE=5242880

# Frontend .env
REACT_APP_API_URL=http://localhost:5000/api
REACT_APP_MAX_IMAGE_SIZE=5
8. Dependencies
8.1 Frontend package.json
jsonCopy{
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "typescript": "^5.0.0",
    "@mui/material": "^5.14.0",
    "react-router-dom": "^6.15.0",
    "axios": "^1.4.0",
    "formik": "^2.4.2",
    "yup": "^1.2.0",
    "react-query": "^3.39.3"
  }
}
8.2 Backend package.json
jsonCopy{
  "dependencies": {
    "express": "^4.18.2",
    "typescript": "^5.0.0",
    "@prisma/client": "^5.1.0",
    "bcryptjs": "^2.4.3",
    "jsonwebtoken": "^9.0.1",
    "multer": "^1.4.5-lts.1",
    "sharp": "^0.32.4"
  }
}
[... continues with deployment, testing, etc. ...]
</specification>
```

STEP 7: Save the Specification

Copy everything between <specification> tags
Save as recipe_app_specification.md
Create a project folder:

Copyrecipe-manager-project/
├── recipe_app_concept.md           # Your original idea
├── sample_code.js                  # Your code samples
└── recipe_app_specification.md     # Generated specification (30-50 pages)

STEP 8: Use with OPAL
Method A: Direct OPAL Platform

Login to OPAL platform
Click "New Project"
Upload recipe_app_specification.md
Select "Full Stack Application"
Click "Generate"

Method B: Via Claude/ChatGPT (if no direct OPAL access)
Start a new conversation:
CopyI have a complete technical specification for a full-stack recipe manager application.
Please generate the application code based on this specification.

[PASTE recipe_app_specification.md]

Please generate in this order:
1. Database setup (Prisma schema and migrations)
2. Backend API (all endpoints and services)
3. Frontend components (all React components)
4. Docker configuration
5. README with complete setup instructions

Generate one section at a time, starting with the database setup.

STEP 9: Review and Refine
If you need changes, go back to Claude with the specification:
CopyLooking at section 5.2.3 (RecipeForm component), please update it to:
- Use a step-by-step wizard instead of single form
- Add image preview before upload
- Include ingredient auto-complete

Please provide the updated component specification.

✅ Expected Results
You should have:

✓ Complete 30-50 page specification
✓ Database schema with all relationships
✓ 20+ frontend components specified
✓ 15+ API endpoints documented
✓ Authentication and security details
✓ Docker deployment configuration
✓ Complete dependency lists
✓ Ready for OPAL to generate full application


Example 3: Converting Existing Code to Specification
📋 Scenario
You have an existing small project (maybe from GitHub or your own code) that you want to expand, but you need a proper specification first.
🎯 Goal
Convert existing code into a comprehensive specification that can be used to regenerate, improve, or expand the application.
📝 Step-by-Step Instructions
STEP 1: Gather Your Existing Code
Let's say you have a simple weather app with these files:
File: index.html
htmlCopy<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Weather App</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h1>Weather App</h1>
        <input type="text" id="city-input" placeholder="Enter city name">
        <button id="search-btn">Search</button>
        <div id="weather-display"></div>
    </div>
    <script src="app.js"></script>
</body>
</html>
File: style.css
cssCopybody {
    font-family: Arial, sans-serif;
    background: linear-gradient(to right, #4facfe, #00f2fe);
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.container {
    background: white;
    padding: 2rem;
    border-radius: 10px;
    box-shadow: 0 4px 6px rgba(0,0,0,0.1);
    text-align: center;
}

#city-input {
    padding: 0.5rem;
    width: 200px;
    margin-right: 0.5rem;
}

button {
    padding: 0.5rem 1rem;
    background: #4facfe;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

#weather-display {
    margin-top: 1rem;
}
File: app.js
javascriptCopyconst API_KEY = 'your-api-key';
const searchBtn = document.getElementById('search-btn');
const cityInput = document.getElementById('city-input');
const weatherDisplay = document.getElementById('weather-display');

searchBtn.addEventListener('click', getWeather);

async function getWeather() {
    const city = cityInput.value;
    if (!city) return;
    
    try {
        const response = await fetch(
            `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${API_KEY}&units=metric`
        );
        const data = await response.json();
        
        displayWeather(data);
    } catch (error) {
        weatherDisplay.innerHTML = '<p>Error fetching weather data</p>';
    }
}

function displayWeather(data) {
    const html = `
        <h2>${data.name}</h2>
        <p>Temperature: ${data.main.temp}°C</p>
        <p>Weather: ${data.weather[0].description}</p>
        <p>Humidity: ${data.main.humidity}%</p>
    `;
    weatherDisplay.innerHTML = html;
}

STEP 2: Combine Your Code into One Document
Create a file called existing_weather_app.md:
markdownCopy# Existing Weather App Code

## Overview
This is a simple weather application that fetches weather data from OpenWeatherMap API.

## Current Features
- Search weather by city name
- Display temperature, weather description, and humidity
- Simple, clean UI

## Files

### index.html
```html
[PASTE YOUR index.html CODE]
style.css
cssCopy[PASTE YOUR style.css CODE]
app.js
javascriptCopy[PASTE YOUR app.js CODE]
Desired Improvements
I want to expand this application with:

5-day forecast display
Geolocation to get current location weather
Save favorite cities (localStorage)
Display weather icons
More detailed weather information (wind speed, pressure, etc.)
Better error handling
Loading states
Responsive design improvements
Dark mode toggle
Unit conversion (Celsius/Fahrenheit)

Copy
---

#### **STEP 3: Open Claude and Load SKILL.md**

1. Go to claude.ai
2. New conversation
3. Paste SKILL.md document

---

#### **STEP 4: Request Specification Generation**

After Claude acknowledges the SKILL.md, paste:
Please analyze this existing code and generate a comprehensive technical specification
that includes both the current implementation and the planned improvements.
<app_description>
Current state: Simple weather app with basic city search
Desired state: Full-featured weather application with forecast, favorites, and enhanced UX
Planned features:

5-day weather forecast
Geolocation for current position
Favorite cities management (localStorage)
Weather condition icons
Extended weather details (wind, pressure, UV index)
Loading and error states
Responsive design (mobile-first)
Dark/light theme toggle
Temperature unit conversion (°C/°F)
Recent searches history
</app_description>

<code_or_spec>
[PASTE ENTIRE CONTENT OF existing_weather_app.md]
</code_or_spec>
Please generate a specification that:

Documents the existing code structure
Expands it with the new features
Maintains backward compatibility
Provides clear migration path
Includes all data models, components, and services needed

Copy
---

#### **STEP 5: Wait for Generation**

Claude will analyze your code and generate a comprehensive specification that:
- Documents what you have
- Specifies what you want to add
- Provides structure for both

---

#### **STEP 6: Review the Generated Specification**

You'll receive something like:

```markdown
<specification>

# Technical Specification: Enhanced Weather Application

## 1. Executive Summary

### 1.1 Current State Analysis
The existing application provides basic weather lookup functionality with:
- Single city weather search
- OpenWeatherMap API integration
- Simple display of temperature, conditions, and humidity
- Gradient blue background design
- Vanilla JavaScript implementation

### 1.2 Enhancement Objectives
Expand the application to include:
- 5-day weather forecast with hourly breakdown
- Geolocation-based automatic weather detection
- Favorite cities management with persistence
- Weather condition icons and visual indicators
- Comprehensive weather metrics
- Enhanced UX with loading states and error handling
- Responsive, mobile-first design
- Theme customization (light/dark mode)
- Temperature unit conversion
- Search history

## 2. Technology Stack

### 2.1 Core Technologies (Unchanged)
- **HTML5**: Semantic markup
- **CSS3**: Modern styling with CSS Grid/Flexbox
- **Vanilla JavaScript (ES6+)**: No framework dependencies

### 2.2 Additional Technologies
- **LocalStorage API**: Data persistence
- **Geolocation API**: User location detection
- **Fetch API**: HTTP requests
- **CSS Custom Properties**: Theme management

### 2.3 External APIs
- **OpenWeatherMap API v2.5**:
  - Current Weather Data endpoint
  - 5 Day / 3 Hour Forecast endpoint
  - Weather Icons
  - Geocoding API (for city search)

## 3. Data Models

### 3.1 Current Weather Data Model
```javascript
interface CurrentWeather {
  city: string;
  country: string;
  temperature: number;
  feelsLike: number;
  tempMin: number;
  tempMax: number;
  humidity: number;
  pressure: number;
  windSpeed: number;
  windDirection: number;
  weatherCondition: string;
  weatherDescription: string;
  weatherIcon: string;
  cloudiness: number;
  visibility: number;
  sunrise: number; // Unix timestamp
  sunset: number; // Unix timestamp
  timezone: number;
  timestamp: number;
}
3.2 Forecast Data Model
javascriptCopyinterface ForecastDay {
  date: string; // ISO date
  tempDay: number;
  tempNight: number;
  tempMin: number;
  tempMax: number;
  weatherCondition: string;
  weatherDescription: string;
  weatherIcon: string;
  humidity: number;
  windSpeed: number;
  pop: number; // Probability of precipitation (0-1)
  hourlyForecasts: HourlyForecast[];
}

interface HourlyForecast {
  time: string; // ISO datetime
  temperature: number;
  weatherIcon: string;
  weatherDescription: string;
  pop: number;
}
3.3 Favorite City Model
javascriptCopyinterface FavoriteCity {
  id: string; // UUID
  name: string;
  country: string;
  lat: number;
  lon: number;
  addedAt: number; // Unix timestamp
  lastUpdated: number;
  currentWeather?: CurrentWeather; // Cached data
}
3.4 Application State Model
javascriptCopyinterface AppState {
  currentWeather: CurrentWeather | null;
  forecast: ForecastDay[];
  favorites: FavoriteCity[];
  searchHistory: SearchHistoryItem[];
  settings: UserSettings;
  ui: UIState;
}

interface UserSettings {
  temperatureUnit: 'celsius' | 'fahrenheit';
  theme: 'light' | 'dark' | 'auto';
  defaultLocation: {
    lat: number;
    lon: number;
    name: string;
  } | null;
}

interface UIState {
  isLoading: boolean;
  error: string | null;
  activeView: 'current' | 'forecast' | 'favorites';
  selectedForecastDay: number;
}

interface SearchHistoryItem {
  city: string;
  timestamp: number;
}
4. UI/UX & Theming
4.1 Design System
Color Palette
cssCopy:root {
  /* Light Theme */
  --color-primary: #4facfe;
  --color-primary-dark: #0093ff;
  --color-secondary: #00f2fe;
  
  --color-bg-primary: #ffffff;
  --color-bg-secondary: #f5f7fa;
  --color-bg-tertiary: #e8f4f8;
  
  --color-text-primary: #2c3e50;
  --color-text-secondary: #546e7a;
  --color-text-muted: #90a4ae;
  
  --color-success: #4caf50;
  --color-warning: #ff9800;
  --color-error: #f44336;
  --color-info: #2196f3;
  
  /* Shadows */
  --shadow-sm: 0 2px 4px rgba(0,0,0,0.1);
  --shadow-md: 0 4px 8px rgba(0,0,0,0.12);
  --shadow-lg: 0 8px 16px rgba(0,0,0,0.15);
  
  /* Border Radius */
  --radius-sm: 4px;
  --radius-md: 8px;
  --radius-lg: 12px;
  --radius-xl: 16px;
  
  /* Spacing */
  --spacing-xs: 0.25rem;
  --spacing-sm: 0.5rem;
  --spacing-md: 1rem;
  --spacing-lg: 1.5rem;
  --spacing-xl: 2rem;
  --spacing-2xl: 3rem;
}

[data-theme="dark"] {
  --color-bg-primary: #1a1a2e;
  --color-bg-secondary: #16213e;
  --color-bg-tertiary: #0f3460;
  
  --color-text-primary: #eaeaea;
  --color-text-secondary: #b8b8b8;
  --color-text-muted: #8a8a8a;
}
4.2 Layout Structure
Copy┌──────────────────────────────────────────┐
│              Header                       │
│  ┌────────────────────┐  ┌──────┐       │
│  │   Search Bar       │  │Theme │       │
│  └────────────────────┘  └──────┘       │
├──────────────────────────────────────────┤
│                                          │
│          Current Weather Card           │
│  ┌────────────────────────────────────┐ │
│  │  City Name                 Icon    │ │
│  │  28°C                              │ │
│  │  Feels like 26°C                   │ │
│  │  ☀ Clear Sky                       │ │
│  │                                    │ │
│  │  [Details Grid]                    │ │
│  │  Humidity: 65%    Wind: 12 km/h   │ │
│  │  Pressure: 1013mb Visibility: 10km│ │
│  └────────────────────────────────────┘ │
│                                          │
├──────────────────────────────────────────┤
│          5-Day Forecast                  │
│  ┌────┐ ┌────┐ ┌────┐ ┌────┐ ┌────┐   │
│  │Mon │ │Tue │ │Wed │ │Thu │ │Fri │   │
│  │ ☀  │ │ ⛅ │ │ 🌧 │ │ ☁  │ │ ☀  │   │
│  │28°C│ │25°C│ │22°C│ │24°C│ │27°C│   │
│  └────┘ └────┘ └────┘ └────┘ └────┘   │
│                                          │
├──────────────────────────────────────────┤
│          Favorite Cities                 │
│  [City Cards...]                         │
└──────────────────────────────────────────┘
5. Component Specifications
5.1 App Component (Main Controller)
javascriptCopyclass WeatherApp {
  constructor() {
    this.state = this.loadState();
    this.api = new WeatherAPIService(API_KEY);
    this.storage = new StorageService();
    this.ui = new UIController();
    
    this.init();
  }
  
  init() {
    this.setupEventListeners();
    this.loadUserPreferences();
    this.checkGeolocation();
    this.loadFavorites();
    
    // Load last viewed city or use geolocation
    if (this.state.settings.defaultLocation) {
      this.loadWeatherByCoordinates(
        this.state.settings.defaultLocation.lat,
        this.state.settings.defaultLocation.lon
      );
    }
  }
  
  setupEventListeners() {
    // Search functionality
    document.getElementById('search-btn').addEventListener('click', () => {
      this.handleSearch();
    });
    
    document.getElementById('city-input').addEventListener('keypress', (e) => {
      if (e.key === 'Enter') this.handleSearch();
    });
    
    // Geolocation button
    document.getElementById('location-btn').addEventListener('click', () => {
      this.handleGeolocation();
    });
    
    // Theme toggle
    document.getElementById('theme-toggle').addEventListener('click', () => {
      this.toggleTheme();
    });
    
    // Unit conversion
    document.getElementById('unit-toggle').addEventListener('click', () => {
      this.toggleUnits();
    });
    
    // Tab navigation
    document.querySelectorAll('.tab-btn').forEach(btn => {
      btn.addEventListener('click', (e) => {
        this.switchTab(e.target.dataset.tab);
      });
    });
  }
  
  async handleSearch() {
    const city = document.getElementById('city-input').value.trim();
    if (!city) return;
    
    this.ui.showLoading();
    
    try {
      const weather = await this.api.getCurrentWeather(city);
      const forecast = await this.api.getForecast(city);
      
      this.state.currentWeather = weather;
      this.state.forecast = forecast;
      
      this.addToSearchHistory(city);
      this.ui.displayWeather(weather, this.state.settings.temperatureUnit);
      this.ui.displayForecast(forecast, this.state.settings.temperatureUnit);
      this.ui.hideLoading();
      
      this.saveState();
    } catch (error) {
      this.ui.showError('Unable to fetch weather data. Please try again.');
      this.ui.hideLoading();
    }
  }
  
  async handleGeolocation() {
    if (!navigator.geolocation) {
      this.ui.showError('Geolocation is not supported by your browser');
      return;
    }
    
    this.ui.showLoading();
    
    navigator.geolocation.getCurrentPosition(
      async (position) => {
        const { latitude, longitude } = position.coords;
        await this.loadWeatherByCoordinates(latitude, longitude);
      },
      (error) => {
        this.ui.showError('Unable to retrieve your location');
        this.ui.hideLoading();
      }
    );
  }
  
  async loadWeatherByCoordinates(lat, lon) {
    try {
      const weather = await this.api.getCurrentWeatherByCoords(lat, lon);
      const forecast = await this.api.getForecastByCoords(lat, lon);
      
      this.state.currentWeather = weather;
      this.state.forecast = forecast;
      
      this.ui.displayWeather(weather, this.state.settings.temperatureUnit);
      this.ui.displayForecast(forecast, this.state.settings.temperatureUnit);
      this.ui.hideLoading();
      
      this.saveState();
    } catch (error) {
      this.ui.showError('Unable to fetch weather data');
      this.ui.hideLoading();
    }
  }
  
  toggleTheme() {
    const themes = ['light', 'dark'];
    const currentIndex = themes.indexOf(this.state.settings.theme);
    const nextTheme = themes[(currentIndex + 1) % themes.length];
    
    this.state.settings.theme = nextTheme;
    document.documentElement.setAttribute('data-theme', nextTheme);
    this.saveState();
  }
  
  toggleUnits() {
    const units = ['celsius', 'fahrenheit'];
    const currentIndex = units.indexOf(this.state.settings.temperatureUnit);
    const nextUnit = units[(currentIndex + 1) % units.length];
    
    this.state.settings.temperatureUnit = nextUnit;
    
    // Re-render with new units
    if (this.state.currentWeather) {
      this.ui.displayWeather(this.state.currentWeather, nextUnit);
    }
    if (this.state.forecast.length > 0) {
      this.ui.displayForecast(this.state.forecast, nextUnit);
    }
    
    this.saveState();
  }
  
  addToFavorites(city) {
    const favorite = {
      id: this.generateUUID(),
      name: city.name,
      country: city.country,
      lat: city.lat,
      lon: city.lon,
      addedAt: Date.now(),
      lastUpdated: Date.now(),
      currentWeather: this.state.currentWeather
    };
    
    this.state.favorites.push(favorite);
    this.ui.renderFavorites(this.state.favorites);
    this.saveState();
  }
  
  removeFromFavorites(cityId) {
    this.state.favorites = this.state.favorites.filter(f => f.id !== cityId);
    this.ui.renderFavorites(this.state.favorites);
    this.saveState();
  }
  
  addToSearchHistory(city) {
    const historyItem = {
      city: city,
      timestamp: Date.now()
    };
    
    // Keep only last 10 searches
    this.state.searchHistory.unshift(historyItem);
    this.state.searchHistory = this.state.searchHistory.slice(0, 10);
    
    this.saveState();
  }
  
  saveState() {
    this.storage.save('weatherAppState', this.state);
  }
  
  loadState() {
    const defaultState = {
      currentWeather: null,
      forecast: [],
      favorites: [],
      searchHistory: [],
      settings: {
        temperatureUnit: 'celsius',
        theme: 'light',
        defaultLocation: null
      },
      ui: {
        isLoading: false,
        error: null,
        activeView: 'current',
        selectedForecastDay: 0
      }
    };
    
    return this.storage.load('weatherAppState', defaultState);
  }
  
  loadUserPreferences() {
    const { theme } = this.state.settings;
    document.documentElement.setAttribute('data-theme', theme);
  }
  
  generateUUID() {
    return 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g, function(c) {
      const r = Math.random() * 16 | 0;
      const v = c == 'x' ? r : (r & 0x3 | 0x8);
      return v.toString(16);
    });
  }
}

// Initialize app when DOM is ready
document.addEventListener('DOMContentLoaded', () => {
  window.weatherApp = new WeatherApp();
});
5.2 WeatherAPIService
javascriptCopyclass WeatherAPIService {
  constructor(apiKey) {
    this.apiKey = apiKey;
    this.baseUrl = 'https://api.openweathermap.org/data/2.5';
  }
  
  async getCurrentWeather(city) {
    const url = `${this.baseUrl}/weather?q=${encodeURIComponent(city)}&appid=${this.apiKey}&units=metric`;
    const response = await fetch(url);
    
    if (!response.ok) {
      throw new Error(`Weather API error: ${response.status}`);
    }
    
    const data = await response.json();
    return this.parseCurrentWeather(data);
  }
  
  async getCurrentWeatherByCoords(lat, lon) {
    const url = `${this.baseUrl}/weather?lat=${lat}&lon=${lon}&appid=${this.apiKey}&units=metric`;
    const response = await fetch(url);
    
    if (!response.ok) {
      throw new Error(`Weather API error: ${response.status}`);
    }
    
    const data = await response.json();
    return this.parseCurrentWeather(data);
  }
  
  async getForecast(city) {
    const url = `${this.baseUrl}/forecast?q=${encodeURIComponent(city)}&appid=${this.apiKey}&units=metric`;
    const response = await fetch(url);
    
    if (!response.ok) {
      throw new Error(`Forecast API error: ${response.status}`);
    }
    
    const data = await response.json();
    return this.parseForecast(data);
  }
  
  async getForecastByCoords(lat, lon) {
    const url = `${this.baseUrl}/forecast?lat=${lat}&lon=${lon}&appid=${this.apiKey}&units=metric`;
    const response = await fetch(url);
    
    if (!response.ok) {
      throw new Error(`Forecast API error: ${response.status}`);
    }
    
    const data = await response.json();
    return this.parseForecast(data);
  }
  
  parseCurrentWeather(data) {
    return {
      city: data.name,
      country: data.sys.country,
      temperature: Math.round(data.main.temp),
      feelsLike: Math.round(data.main.feels_like),
      tempMin: Math.round(data.main.temp_min),
      tempMax: Math.round(data.main.temp_max),
      humidity: data.main.humidity,
      pressure: data.main.pressure,
      windSpeed: data.wind.speed,
      windDirection: data.wind.deg,
      weatherCondition: data.weather[0].main,
      weatherDescription: data.weather[0].description,
      weatherIcon: data.weather[0].icon,
      cloudiness: data.clouds.all,
      visibility: data.visibility,
      sunrise: data.sys.sunrise,
      sunset: data.sys.sunset,
      timezone: data.timezone,
      timestamp: data.dt
    };
  }
  
  parseForecast(data) {
    // Group forecasts by day
    const forecastsByDay = {};
    
    data.list.forEach(item => {
      const date = new Date(item.dt * 1000).toISOString().split('T')[0];
      
      if (!forecastsByDay[date]) {
        forecastsByDay[date] = {
          date: date,
          temperatures: [],
          weather: [],
          hourly: []
        };
      }
      
      forecastsByDay[date].temperatures.push(item.main.temp);
      forecastsByDay[date].weather.push({
        condition: item.weather[0].main,
        description: item.weather[0].description,
        icon: item.weather[0].icon
      });
      forecastsByDay[date].hourly.push({
        time: new Date(item.dt * 1000).toISOString(),
        temperature: Math.round(item.main.temp),
        weatherIcon: item.weather[0].icon,
        weatherDescription: item.weather[0].description,
        pop: item.pop || 0
      });
    });
    
    // Convert to array and calculate daily summaries
    return Object.values(forecastsByDay).slice(0, 5).map(day => {
      const temps = day.temperatures;
      return {
        date: day.date,
        tempDay: Math.round(temps.reduce((a, b) => a + b) / temps.length),
        tempNight: Math.round(Math.min(...temps)),
        tempMin: Math.round(Math.min(...temps)),
        tempMax: Math.round(Math.max(...temps)),
        weatherCondition: day.weather[0].condition,
        weatherDescription: day.weather[0].description,
        weatherIcon: day.weather[0].icon,
        humidity: 0, // Would need to calculate from hourly
        windSpeed: 0, // Would need to calculate from hourly
        pop: day.hourly.reduce((max, h) => Math.max(max, h.pop), 0),
        hourlyForecasts: day.hourly
      };
    });
  }
  
  getWeatherIconUrl(iconCode) {
    return `https://openweathermap.org/img/wn/${iconCode}@2x.png`;
  }
}
[... specification continues for 40+ more pages with:

UIController class
StorageService class
Complete HTML structure
Complete CSS with all components
Responsive design breakpoints
Animation specifications
Error handling
Loading states
Accessibility features
Testing recommendations
Deployment instructions
...]

</specification>
```

STEP 7: Save and Use

Save as enhanced_weather_app_specification.md
You now have a complete blueprint to:

Rebuild the application with improvements
Hand off to another developer
Use with OPAL to generate enhanced version




STEP 8: Generate Enhanced Application with OPAL
New conversation in Claude/ChatGPT:
CopyPlease generate the complete code for this enhanced weather application based on the specification.

[PASTE enhanced_weather_app_specification.md]

Generate in this order:
1. Complete HTML file (index.html)
2. Complete CSS file (style.css) with all theme support
3. Complete JavaScript (app.js, weatherApi.js, storage.js, ui.js)
4. README.md with:
   - Setup instructions
   - API key configuration
   - Feature list
   - Browser compatibility

Start with index.html.

✅ Expected Results

✓ Complete specification of existing code
✓ Blueprint for all enhancements
✓ Ready to regenerate improved version
✓ Can be used as documentation
✓ Ready for OPAL or manual development


Example 4: Specification for Mobile App (React Native)
📋 Scenario
You want to create a fitness tracking mobile app and need a specification for both iOS and Android.
🎯 Goal
Generate a cross-platform mobile app specification using React Native.
📝 Step-by-Step Instructions
STEP 1: Create App Description
Create fitness_tracker_requirements.md:
markdownCopy# Fitness Tracker Mobile App

## Overview
A cross-platform mobile fitness tracking application for iOS and Android with workout logging, progress tracking, and social features.

## Target Platforms
- iOS 13.0+
- Android 8.0+
- Tablet support

## Core Features

### 1. User Management
- Email/password registration
- Social login (Google, Apple, Facebook)
- User profile with photo
- Bio, fitness goals, stats
- Privacy settings

### 2. Workout Tracking
- Start/stop workout sessions
- Track workout duration
- Record exercises:
  - Exercise name
  - Sets and reps
  - Weight used
  - Rest time
  - Notes
- Built-in exercise library with:
  - Exercise descriptions
  - GIF demonstrations
  - Muscle group targeting
  - Equipment needed

### 3. Workout History
- Calendar view of all workouts
- Detailed workout logs
- Statistics and trends
- Personal records tracking
- Progress photos

### 4. Progress Tracking
- Body weight tracking
- Body measurements
- Progress photos with date
- Charts and graphs:
  - Weight over time
  - Strength progress per exercise
  - Workout frequency
  - Volume progression

### 5. Workout Plans
- Pre-built workout programs
- Create custom workout plans
- Schedule workouts on calendar
- Workout reminders/notifications

### 6. Social Features
- Follow other users
- Share workouts (optional)
- Like and comment on posts
- Achievement badges
- Leaderboards

### 7. Premium Features (In-App Purchase)
- Advanced analytics
- Unlimited workout plans
- Export data
- No ads
- Custom themes

## Technical Requirements

### Frontend
- **Framework**: React Native 0.72+
- **Language**: TypeScript
- **Navigation**: React Navigation 6
- **State Management**: Redux Toolkit + RTK Query
- **UI Components**: React Native Paper
- **Charts**: Victory Native
- **Forms**: React Hook Form
- **Camera**: React Native Vision Camera
- **Animations**: React Native Reanimated

### Backend
- **Runtime**: Node.js 18 LTS
- **Framework**: Express.js
- **Database**: PostgreSQL
- **ORM**: Prisma
- **Authentication**: JWT + OAuth2
- **File Storage**: AWS S3 or similar
- **Push Notifications**: Firebase Cloud Messaging

### Infrastructure
- **API**: RESTful API
- **Real-time**: WebSockets for social features
- **Caching**: Redis
- **CDN**: CloudFlare for images
- **Analytics**: Firebase Analytics
- **Crash Reporting**: Sentry

## Design Requirements
- Material Design 3 (Android)
- Human Interface Guidelines (iOS)
- Dark mode support
- Offline functionality
- Smooth animations (60 FPS)
- Haptic feedback
- Gesture navigation

## Performance Requirements
- App launch: < 2 seconds
- Screen transitions: < 300ms
- API responses: < 1 second
- Offline-first architecture
- Optimized images
- Lazy loading

## Security
- Secure credential storage
- HTTPS only
- Data encryption at rest
- Secure file uploads
- Rate limiting
- Input validation

STEP 2: Add UI Mockup Descriptions (Optional but Helpful)
Create ui_mockups_description.md:
markdownCopy# UI Screen Descriptions

## 1. Welcome/Onboarding
- Splash screen with app logo
- 3-screen onboarding with swipe:
  - Screen 1: "Track Your Workouts"
  - Screen 2: "See Your Progress"
  - Screen 3: "Achieve Your Goals"
- Skip button
- Get Started button

## 2. Authentication Screens

### Login Screen
- Logo at top
- Email input
- Password input (with show/hide)
- Login button
- Forgot password link
- Or divider
- Social login buttons (Google, Apple, Facebook)
- Don't have account? Sign up link

### Register Screen
- Back button
- Full name input
- Email input
- Password input (with strength indicator)
- Confirm password input
- Terms acceptance checkbox
- Sign up button
- Already have account? Login link

## 3. Main App Navigation (Bottom Tabs)

### Tab 1: Home/Dashboard
- Greeting: "Hey, [Name]!"
- Quick stats cards:
  - Workouts this week
  - Current streak
  - Total weight lifted
- Today's planned workout card
- Start workout button (prominent)
- Recent activity feed

### Tab 2: Workouts
- Search bar
- Filter chips (All, Strength, Cardio, Flexibility)
- Workout history list:
  - Date
  - Workout name
  - Duration
  - Number of exercises
- Floating Action Button: New Workout

### Tab 3: Progress
- Date range selector
- Chart tabs: Weight, Strength, Volume
- Interactive charts
- Progress photos gallery
- Export data button

### Tab 4: Plans
- My Plans section
- Discover Programs section
- Program cards with:
  - Program name
  - Duration
  - Difficulty
  - Description
- Create Plan button

### Tab 5: Profile
- Profile photo (tap to edit)
- User name and bio
- Stats row: Followers, Following, Workouts
- Settings button
- Sections:
  - My Achievements
  - Premium Upgrade
  - Settings
  - Help & Support
  - Logout

## 4. Workout Tracking Screen
- Header with workout name and timer
- Exercise list:
  - Exercise name with muscle group icon
  - Sets/reps display
  - Checkboxes for completed sets
  - Weight input
  - Notes field
- Add exercise button
- Rest timer (popup)
- Finish workout button

## 5. Exercise Library Screen
- Search bar
- Filter by muscle group
- Filter by equipment
- Exercise cards:
  - GIF preview
  - Exercise name
  - Muscle groups (chips)
  - Equipment needed
- Tap for exercise details

## 6. Progress Photo Screen
- Photo grid (2 columns)
- Add photo button
- Each photo shows:
  - Date
  - Weight (if tracked)
- Tap to view full screen with:
  - Comparison slider
  - Share options

STEP 3: Open Claude with SKILL.md

Go to claude.ai
New conversation
Paste SKILL.md


STEP 4: Request Mobile App Specification
CopyPlease generate a comprehensive technical specification for a React Native mobile application.

<app_description>
[PASTE fitness_tracker_requirements.md]

[PASTE ui_mockups_description.md]

Additional context:
- This should be production-ready specification
- Include complete navigation structure
- Include all Redux slices and API endpoints
- Include Prisma database schema
- Include deployment configuration for App Store and Play Store
- Include CI/CD pipeline specifications
</app_description>

<code_or_spec>
# No existing code - generate from requirements
</code_or_spec>

Please ensure the specification includes:
1. Complete React Native project structure
2. All screen components with full implementations
3. Navigation configuration
4. Redux store structure
5. API service layer
6. Database models and relationships
7. Authentication flow
8. Push notification setup
9. App store deployment guides
10. Testing strategy

STEP 5: Wait for Generation
This will take 90-120 seconds due to complexity. Claude will generate 50-70 pages.

STEP 6: Review Mobile-Specific Sections
The specification will include mobile-specific sections like:
markdownCopy## 2. Technology Stack

### 2.1 React Native Configuration

```json
// package.json
{
  "name": "fitness-tracker",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "android": "react-native run-android",
    "ios": "react-native run-ios",
    "start": "react-native start",
    "test": "jest",
    "lint": "eslint .",
    "type-check": "tsc --noEmit"
  },
  "dependencies": {
    "react": "18.2.0",
    "react-native": "0.72.6",
    "@react-navigation/native": "^6.1.9",
    "@react-navigation/bottom-tabs": "^6.5.11",
    "@react-navigation/stack": "^6.3.20",
    "@reduxjs/toolkit": "^1.9.7",
    "react-redux": "^8.1.3",
    "react-native-paper": "^5.11.1",
    "react-native-vector-icons": "^10.0.2",
    "react-native-reanimated": "^3.5.4",
    "react-native-gesture-handler": "^2.13.4",
    "react-native-vision-camera": "^3.6.3",
    "victory-native": "^36.8.6",
    "react-hook-form": "^7.48.2",
    "@react-native-async-storage/async-storage": "^1.19.5",
    "axios": "^1.6.2",
    "react-native-push-notification": "^8.1.1"
  },
  "devDependencies": {
    "@types/react": "^18.2.37",
    "@types/react-native": "^0.72.6",
    "typescript": "^5.2.2",
    "@typescript-eslint/eslint-plugin": "^6.10.0",
    "@typescript-eslint/parser": "^6.10.0",
    "jest": "^29.7.0",
    "@testing-library/react-native": "^12.4.0"
  }
}
3. Data Models
3.1 React Native Local Models
typescriptCopy// types/workout.ts
export interface Workout {
  id: string;
  userId: string;
  name: string;
  startTime: Date;
  endTime?: Date;
  duration?: number; // minutes
  exercises: WorkoutExercise[];
  notes?: string;
  createdAt: Date;
  updatedAt: Date;
  synced: boolean; // For offline support
}

export interface WorkoutExercise {
  id: string;
  exerciseId: string;
  exerciseName: string;
  muscleGroups: string[];
  sets: ExerciseSet[];
  order: number;
}

export interface ExerciseSet {
  id: string;
  setNumber: number;
  reps: number;
  weight?: number;
  weightUnit: 'kg' | 'lbs';
  completed: boolean;
  restTime?: number; // seconds
  notes?: string;
}

export interface Exercise {
  id: string;
  name: string;
  description: string;
  muscleGroups: MuscleGroup[];
  equipment: Equipment[];
  difficulty: 'beginner' | 'intermediate' | 'advanced';
  gifUrl?: string;
  videoUrl?: string;
  instructions: string[];
}

export enum MuscleGroup {
  CHEST = 'chest',
  BACK = 'back',
  SHOULDERS = 'shoulders',
  BICEPS = 'biceps',
  TRICEPS = 'triceps',
  LEGS = 'legs',
  CORE = 'core',
  CARDIO = 'cardio'
}

export enum Equipment {
  BARBELL = 'barbell',
  DUMBBELL = 'dumbbell',
  MACHINE = 'machine',
  BODYWEIGHT = 'bodyweight',
  RESISTANCE_BAND = 'resistance_band',
  KETTLEBELL = 'kettlebell',
  CABLE = 'cable'
}

// types/user.ts
export interface User {
  id: string;
  email: string;
  fullName: string;
  username: string;
  avatarUrl?: string;
  bio?: string;
  fitnessGoals: FitnessGoal[];
  stats: UserStats;
  preferences: UserPreferences;
  isPremium: boolean;
  createdAt: Date;
}

export interface UserStats {
  totalWorkouts: number;
  currentStreak: number;
  longestStreak: number;
  totalWeight: number; // Total weight lifted
  totalDuration: number; // Total workout minutes
  followersCount: number;
  followingCount: number;
}

export interface UserPreferences {
  weightUnit: 'kg' | 'lbs';
  theme: 'light' | 'dark' | 'auto';
  notificationsEnabled: boolean;
  workoutReminders: boolean;
  reminderTime?: string; // HH:mm format
  privacyMode: 'public' | 'private' | 'friends';
}

export interface FitnessGoal {
  id: string;
  type: 'weight' | 'strength' | 'endurance' | 'custom';
  target: number;
  current: number;
  unit: string;
  deadline?: Date;
  completed: boolean;
}

// types/progress.ts
export interface BodyWeight {
  id: string;
  userId: string;
  weight: number;
  unit: 'kg' | 'lbs';
  date: Date;
  notes?: string;
}

export interface ProgressPhoto {
  id: string;
  userId: string;
  imageUrl: string;
  weight?: number;
  date: Date;
  notes?: string;
  visibility: 'private' | 'public';
}

export interface BodyMeasurement {
  id: string;
  userId: string;
  date: Date;
  measurements: {
    chest?: number;
    waist?: number;
    hips?: number;
    biceps?: number;
    thighs?: number;
    calves?: number;
  };
  unit: 'cm' | 'inches';
}
3.2 Backend Database Schema (Prisma)
prismaCopy// prisma/schema.prisma
generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

model User {
  id            String    @id @default(uuid())
  email         String    @unique
  passwordHash  String
  fullName      String
  username      String    @unique
  avatarUrl     String?
  bio           String?
  isPremium     Boolean   @default(false)
  createdAt     DateTime  @default(now())
  updatedAt     DateTime  @updatedAt
  
  // Relations
  workouts          Workout[]
  bodyWeights       BodyWeight[]
  progressPhotos    ProgressPhoto[]
  bodyMeasurements  BodyMeasurement[]
  workoutPlans      WorkoutPlan[]
  socialPosts       SocialPost[]
  followers         Follow[]          @relation("UserFollowers")
  following         Follow[]          @relation("UserFollowing")
  achievements      UserAchievement[]
  preferences       UserPreferences?
  
  @@index([email])
  @@index([username])
}

model UserPreferences {
  id                    String   @id @default(uuid())
  userId                String   @unique
  user                  User     @relation(fields: [userId], references: [id], onDelete: Cascade)
  
  weightUnit            String   @default("kg") // kg or lbs
  theme                 String   @default("auto") // light, dark, auto
  notificationsEnabled  Boolean  @default(true)
  workoutReminders      Boolean  @default(true)
  reminderTime          String?  // HH:mm format
  privacyMode           String   @default("public") // public, private, friends
  
  createdAt             DateTime @default(now())
  updatedAt             DateTime @updatedAt
}

model Workout {
  id          String    @id @default(uuid())
  userId      String
  user        User      @relation(fields: [userId], references: [id], onDelete: Cascade)
  
  name        String
  startTime   DateTime
  endTime     DateTime?
  duration    Int?      // minutes
  notes       String?
  
  exercises   WorkoutExercise[]
  
  createdAt   DateTime  @default(now())
  updatedAt   DateTime  @updatedAt
  
  @@index([userId])
  @@index([startTime])
}

model WorkoutExercise {
  id             String    @id @default(uuid())
  workoutId      String
  workout        Workout   @relation(fields: [workoutId], references: [id], onDelete: Cascade)
  exerciseId     String
  exercise       Exercise  @relation(fields: [exerciseId], references: [id])
  
  order          Int
  sets           ExerciseSet[]
  
  @@index([workoutId])
  @@index([exerciseId])
}

model ExerciseSet {
  id                String            @id @default(uuid())
  workoutExerciseId String
  workoutExercise   WorkoutExercise   @relation(fields: [workoutExerciseId], references: [id], onDelete: Cascade)
  
  setNumber         Int
  reps              Int
  weight            Float?
  weightUnit        String            @default("kg")
  completed         Boolean           @default(false)
  restTime          Int?              // seconds
  notes             String?
  
  @@index([workoutExerciseId])
}

model Exercise {
  id              String    @id @default(uuid())
  name            String
  description     String
  muscleGroups    String[]  // Array of muscle groups
  equipment       String[]  // Array of equipment
  difficulty      String    // beginner, intermediate, advanced
  gifUrl          String?
  videoUrl        String?
  instructions    String[]
  isCustom        Boolean   @default(false)
  createdById     String?
  
  workoutExercises WorkoutExercise[]
  
  @@index([name])
}

model BodyWeight {
  id        String    @id @default(uuid())
  userId    String
  user      User      @relation(fields: [userId], references: [id], onDelete: Cascade)
  
  weight    Float
  unit      String    @default("kg")
  date      DateTime
  notes     String?
  
  createdAt DateTime  @default(now())
  
  @@index([userId])
  @@index([date])
}

model ProgressPhoto {
  id         String    @id @default(uuid())
  userId     String
  user       User      @relation(fields: [userId], references: [id], onDelete: Cascade)
  
  imageUrl   String
  weight     Float?
  date       DateTime
  notes      String?
  visibility String    @default("private") // private, public
  
  createdAt  DateTime  @default(now())
  
  @@index([userId])
  @@index([date])
}

model BodyMeasurement {
  id           String    @id @default(uuid())
  userId       String
  user         User      @relation(fields: [userId], references: [id], onDelete: Cascade)
  
  date         DateTime
  chest        Float?
  waist        Float?
  hips         Float?
  biceps       Float?
  thighs       Float?
  calves       Float?
  unit         String    @default("cm") // cm or inches
  
  createdAt    DateTime  @default(now())
  
  @@index([userId])
  @@index([date])
}

model WorkoutPlan {
  id           String    @id @default(uuid())
  userId       String?
  user         User?     @relation(fields: [userId], references: [id], onDelete: SetNull)
  
  name         String
  description  String
  duration     Int       // weeks
  difficulty   String    // beginner, intermediate, advanced
  isPublic     Boolean   @default(false)
  isPremium    Boolean   @default(false)
  
  schedule     Json      // Weekly schedule
  
  createdAt    DateTime  @default(now())
  updatedAt    DateTime  @updatedAt
  
  @@index([userId])
}

model Follow {
  id          String    @id @default(uuid())
  followerId  String
  follower    User      @relation("UserFollowing", fields: [followerId], references: [id], onDelete: Cascade)
  followingId String
  following   User      @relation("UserFollowers", fields: [followingId], references: [id], onDelete: Cascade)
  
  createdAt   DateTime  @default(now())
  
  @@unique([followerId, followingId])
  @@index([followerId])
  @@index([followingId])
}

model SocialPost {
  id          String    @id @default(uuid())
  userId      String
  user        User      @relation(fields: [userId], references: [id], onDelete: Cascade)
  
  content     String
  workoutId   String?
  imageUrls   String[]
  
  likesCount  Int       @default(0)
  commentsCount Int     @default(0)
  
  createdAt   DateTime  @default(now())
  updatedAt   DateTime  @updatedAt
  
  @@index([userId])
  @@index([createdAt])
}

model Achievement {
  id              String            @id @default(uuid())
  name            String
  description     String
  iconUrl         String
  criteria        Json              // Criteria for achieving
  
  userAchievements UserAchievement[]
}

model UserAchievement {
  id             String       @id @default(uuid())
  userId         String
  user           User         @relation(fields: [userId], references: [id], onDelete: Cascade)
  achievementId  String
  achievement    Achievement  @relation(fields: [achievementId], references: [id])
  
  earnedAt       DateTime     @default(now())
  
  @@unique([userId, achievementId])
  @@index([userId])
}
5. Component Specifications
5.1 Screen Components
5.1.1 HomeScreen Component
typescriptCopy// src/screens/HomeScreen.tsx
import React, { useEffect } from 'react';
import {
  View,
  ScrollView,
  StyleSheet,
  RefreshControl
} from 'react-native';
import {
  Text,
  Card,
  Button,
  Avatar,
  useTheme
} from 'react-native-paper';
import { useAppDispatch, useAppSelector } from '../hooks/redux';
import { fetchUserStats, fetchTodayWorkout } from '../store/slices/userSlice';
import { WorkoutCard } from '../components/WorkoutCard';
import { StatCard } from '../components/StatCard';
import { RecentActivityFeed } from '../components/RecentActivityFeed';

export const HomeScreen: React.FC = () => {
  const theme = useTheme();
  const dispatch = useAppDispatch();
  
  const { user, stats, todayWorkout, loading } = useAppSelector(
    state => state.user
  );
  
  const [refreshing, setRefreshing] = React.useState(false);
  
  useEffect(() => {
    loadData();
  }, []);
  
  const loadData = async () => {
    await Promise.all([
      dispatch(fetchUserStats()),
      dispatch(fetchTodayWorkout())
    ]);
  };
  
  const onRefresh = async () => {
    setRefreshing(true);
    await loadData();
    setRefreshing(false);
  };
  
  const handleStartWorkout = () => {
    navigation.navigate('WorkoutTracking', {
      workoutId: todayWorkout?.id
    });
  };
  
  return (
    <ScrollView
      style={styles.container}
      refreshControl={
        <RefreshControl refreshing={refreshing} onRefresh={onRefresh} />
      }
    >
      {/* Greeting Header */}
      <View style={styles.header}>
        <View>
          <Text variant="headlineMedium" style={styles.greeting}>
            Hey, {user?.fullName.split(' ')[0]}! 👋
          </Text>
          <Text variant="bodyMedium" style={styles.subgreeting}>
            Ready to crush your workout today?
          </Text>
        </View>
        <Avatar.Image
          size={56}
          source={{ uri: user?.avatarUrl || 'default-avatar-url' }}
        />
      </View>
      
      {/* Quick Stats */}
      <View style={styles.statsContainer}>
        <StatCard
          title="Workouts"
          value={stats?.totalWorkouts || 0}
          subtitle="This Week"
          icon="dumbbell"
          color={theme.colors.primary}
        />
        <StatCard
          title="Streak"
          value={stats?.currentStreak || 0}
          subtitle="Days"
          icon="fire"
          color="#FF6B35"
        />
        <StatCard
          title="Weight"
          value={`${stats?.totalWeight || 0}kg`}
          subtitle="This Month"
          icon
