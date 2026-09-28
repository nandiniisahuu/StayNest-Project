# 🏡 StayNest — AI-Powered Property Booking Platform

A full-stack StayNest property booking web application built with **Node.js, Express.js, EJS, MongoDB, Tailwind CSS, and Google Gemini AI**.

The application provides separate **Guest and Host experiences**, property management, favourites, booking and cancellation functionality, flexible home searching, image uploads, authentication, and AI-powered property description generation.

---

# 🚀 Features

## 👤 Guest Features

- User signup and login
- Browse available homes
- View detailed property information
- Add/remove properties from favourites
- Book a home
- View **My Bookings**
- Cancel bookings
- Flexible home search and filtering
- Natural-language home search
- AI Home Finder
- Responsive and improved user interface
- Guest-specific navigation and actions

---

## 🏠 Host Features

- Host login
- Add properties
- Edit properties
- Delete properties
- Upload property images
- Generate AI-powered property descriptions
- View bookings for host properties
- Cancel bookings
- Host users are redirected to the **Host Home List**
- Host interface is separated from the guest experience
- Hosts do not see guest-only **AI Home Finder** and **Book Home** actions

---

# 🤖 AI Features

The project integrates **Google Gemini API** to provide AI-powered functionality.

## 1. AI Property Description Generator

Hosts can generate professional property descriptions using property information.

The application sends property details to the Gemini API and receives an AI-generated description.

---

## 2. AI Home Finder

Guests can search for properties using natural-language queries.

### Example

```text
Singapore me 11000 ke andar 4+ rating wala home
```

The application extracts:

```text
Location          → Singapore
Maximum Price     → 11000
Minimum Rating    → 4
```

The application identifies the search requirements and filters available properties.

The current implementation uses **rule-based JavaScript parsing + MongoDB queries** for structured searches.

This approach allows common searches to work without sending every request to Gemini.

---

# 🔌 APIs Used

The project uses the following APIs/services.

---

## Google Gemini API

Used for:

- AI-generated property descriptions
- AI-powered application functionality

Technology used:

```text
Google Gemini API
@google/genai
```

The Gemini API key is stored securely in the `.env` file.

```env
GEMINI_API_KEY=your_gemini_api_key
```

---

## Internal REST API

The application also contains its own backend API routes.

### AI API Base Path

```text
/api/ai
```

This route connects the frontend/application logic with the Gemini AI service.

### API Architecture

```text
Frontend
   ↓
Express.js API Route
   ↓
Controller
   ↓
AI Service
   ↓
Google Gemini API
```

---

## MongoDB Atlas

MongoDB Atlas is used as the application's cloud database.

It stores:

- Users
- Properties
- Bookings
- Favourites
- Sessions

> MongoDB Atlas is **not an AI API**. It is the application's database service.

---

# 🛠️ Tech Stack

## Frontend

- HTML5
- CSS3
- EJS
- Tailwind CSS
- JavaScript
- Font Awesome

---

## Backend

- Node.js
- Express.js

---

## Database

- MongoDB
- MongoDB Atlas
- Mongoose

---

## Authentication & Sessions

- Express Session
- connect-mongodb-session
- bcryptjs

---

## AI

- Google Gemini API
- `@google/genai`

---

## File Upload

- Multer

---

## Development Tools

- Nodemon
- Git
- GitHub
- VS Code

---

# 🔐 Authentication

The application uses **session-based authentication**.

Sessions are managed using:

```text
express-session
connect-mongodb-session
```

Passwords are securely hashed using:

```text
bcryptjs
```

The application also separates permissions between:

```text
Guest
Host
```

Protected routes prevent unauthorized users from accessing host-specific functionality.

---

# 🖼️ Image Upload

Property images are uploaded using **Multer**.

Supported image types:

```text
PNG
JPG
JPEG
```

Uploaded property images are stored in:

```text
uploads/
```

Hosts can upload property images while creating or editing properties.

---

# ⚙️ Installation & Setup

Follow the steps below to install and run the StayNest project locally.

---

## 📋 Prerequisites

Make sure the following are installed on your system:

- **Node.js** (20 or later recommended)
- **npm**
- **MongoDB Atlas account**
- **Git**
- **VS Code** (recommended)

You can verify Node.js and npm installation using:

```bash
node -v
npm -v
```

---

## 📥 1. Clone the Repository

Clone the project from GitHub:

```bash
git clone https://github.com/nandiniisahuu/StayNest-Project.git
```

Navigate to the project directory:

```bash
cd StayNest-Project
```

---

## 📦 2. Install Dependencies

Install all required Node.js dependencies:

```bash
npm install
```

This installs the packages required for:

- Express.js
- EJS
- MongoDB / Mongoose
- Tailwind CSS
- Google Gemini API
- Authentication
- Sessions
- Image uploads
- Other backend functionality

---

## 🔐 3. Configure Environment Variables

Create a `.env` file in the project root directory.

```text
StayNest-Project/
├── .env
├── app.js
├── package.json
├── routes/
├── controllers/
├── models/
├── views/
├── public/
└── uploads/
```

Add the following environment variables:

```env
MONGO_URI=your_mongodb_atlas_connection_string
JWT_SECRET=your_secret_key
GEMINI_API_KEY=your_gemini_api_key
```

### Environment Variables

| Variable         | Purpose                                                                 |
| ---------------- | ----------------------------------------------------------------------- |
| `MONGO_URI`      | MongoDB Atlas connection string                                         |
| `JWT_SECRET`     | Secret value used for application authentication/security configuration |
| `GEMINI_API_KEY` | Google Gemini API key used for AI-powered features                      |

### Important

Do **not** upload your real `.env` file or API keys to GitHub.

The `.env` file should remain private.

---

## 🍃 4. Configure MongoDB Atlas

StayNest uses **MongoDB Atlas** as its cloud database.

### Steps

1. Create a MongoDB Atlas account.
2. Create a cluster.
3. Create a database user.
4. Allow your IP address in **Network Access**.
5. Copy the MongoDB connection string.
6. Add the connection string to `.env`:

```env
MONGO_URI=mongodb+srv://<username>:<password>@<cluster-url>/<database>
```

The application automatically connects to MongoDB when the server starts.

MongoDB stores application data such as:

- Users
- Homes / Properties
- Bookings
- Favourites
- Sessions

---

## 🤖 5. Configure Google Gemini API

The AI features require a Google Gemini API key.

Create/get an API key from **Google AI Studio** and add it to `.env`:

```env
GEMINI_API_KEY=your_gemini_api_key
```

The Gemini API is used for:

- AI Property Description Generator
- AI-powered property functionality

The API key is accessed server-side through the environment variable and should not be exposed in frontend code.

---

# ▶️ Project Run Steps

After completing the setup, follow these steps to run StayNest.

---

## 1. Open the Project

```bash
cd StayNest-Project
```

---

## 2. Install Dependencies

If dependencies have not already been installed:

```bash
npm install
```

---

## 3. Build Tailwind CSS

Generate the Tailwind CSS output file:

```bash
npm run build
```

This runs:

```bash
npm run tailwind
```

and generates:

```text
public/output.css
```

---

## 4. Start the Application

Start the Node.js/Express server:

```bash
npm start
```

The application will start on:

```text
http://localhost:3003
```

Open the URL in your browser:

```text
http://localhost:3003
```

---

## 🔄 Development Mode

For development, the project also includes **Nodemon**.

You can run the application using:

```bash
npx nodemon app.js
```

Nodemon automatically restarts the server when relevant project files are changed.

---

# 🧪 Quick Start

For a fresh setup, the complete sequence is:

```bash
git clone https://github.com/nandiniisahuu/StayNest-Project.git

cd StayNest-Project

npm install

npm run build

npm start
```

Then open:

```text
http://localhost:3003
```

---

# ⚠️ Troubleshooting

## MongoDB connection error

Check that:

- `MONGO_URI` is correct.
- Your MongoDB Atlas cluster is running.
- Your IP address is allowed in MongoDB Atlas Network Access.
- The database username and password are correct.

---

## Gemini AI features not working

Check that:

```env
GEMINI_API_KEY=your_gemini_api_key
```

is present in the `.env` file and that the API key is valid.

---

## Tailwind styles are not appearing

Run:

```bash
npm run build
```

Then restart the application:

```bash
npm start
```

---

## Port already in use

StayNest runs on port `3003`.

If another application is already using this port, stop that application before starting StayNest.

---

# 🌐 Application URL

Once the server is running:

**Local Application:**

```text
http://localhost:3003
```

The application provides separate experiences for:

- 👤 Guests
- 🏠 Hosts

Guests can browse, search, favourite, book, and manage bookings.

Hosts can manage properties, upload images, generate AI descriptions, and manage property bookings.

---

# 🎯 Project Objectives

This project demonstrates practical full-stack development concepts including:

- Full-stack web development
- Node.js
- Express.js
- EJS
- REST API development
- MVC-style architecture
- MongoDB integration
- Mongoose
- Authentication and authorization
- Session management
- CRUD operations
- Image uploads
- Booking management
- Favourites
- Flexible search and filtering
- Natural-language search parsing
- AI API integration
- Google Gemini integration
- Responsive UI development
- Tailwind CSS
- Git and GitHub

---

# 💡 Learning Outcomes

Through this project, I gained practical experience with:

```text
Node.js
Express.js
EJS
MongoDB
MongoDB Atlas
Mongoose
REST APIs
Authentication
Authorization
Sessions
CRUD Operations
File Uploads
Booking Systems
Search & Filtering
AI API Integration
Google Gemini API
Tailwind CSS
Git
GitHub
```

The project demonstrates how **frontend, backend, database, authentication, file handling, search functionality, and AI services** can work together in a complete full-stack web application.

---

# 👩‍💻 Author

**Nandini**

Interested in **Full Stack Development, Java, Web Development, REST APIs, MongoDB, and AI-powered applications**.
