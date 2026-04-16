# 📚 Flash Card App

A full-stack flashcard application built with **Node.js**, **Express**, and **Vanilla JavaScript**. Create, manage, and organize flashcards with images, protected by JWT authentication.

## Features

✨ **Core Features:**
- 🔐 JWT Token-based Authentication
- 📸 Image Upload Support (Multer)
- 📝 Create Flashcards with Title, Subject, and Category
- 🗑️ Delete Flashcards
- 🎨 Beautiful, Responsive UI
- 💾 Persistent Data Storage (JSON file)
- 🌐 RESTful API Backend

## Tech Stack

**Backend:**
- Node.js
- Express.js
- JWT (JSON Web Tokens)
- Multer (File Upload)
- CORS

**Frontend:**
- HTML5
- CSS3
- Vanilla JavaScript
- Fetch API

## Project Structure

```
flash-card/
├── app.js                 # Main Express server & API routes
├── index.html            # Frontend UI
├── middleware/
│   └── auth.js          # JWT Authentication middleware
├── uploads/             # Directory for uploaded images
├── package.json         # Project dependencies
├── students.json        # Data storage file (auto-created)
└── README.md           # This file
```

## Installation & Setup

### Prerequisites
- Node.js (v12 or higher)
- npm

### Steps

1. **Clone/Download the project:**
   ```bash
   cd flash-card
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Create uploads directory (if not exist):**
   ```bash
   mkdir uploads
   ```

4. **Start the server:**
   ```bash
   npm start
   ```
   OR
   ```bash
   npm run dev
   ```

5. **Open your browser:**
   ```
   http://localhost:3000
   ```

## How to Use

### Step 1: Login
- Click "Login (Get Token)" to generate a JWT token
- Token is saved to browser's localStorage
- Token is valid for 1 hour

### Step 2: Add Flashcards
- Fill in Flashcard Title (e.g., "Biology Basics")
- Enter Subject/Course (e.g., "Biology")
- Specify Category/Location (e.g., "10th Grade")
- Upload an Image
- Click "Add Flashcard" button

### Step 3: View & Manage
- See all flashcards in the grid below
- Hover over cards for animation effects
- Click Delete button to remove a flashcard
- Logout anytime to clear token and session

## API Endpoints

### Authentication
```
POST /login
- Request: None
- Response: { token: "jwt_token_here" }
- Description: Get JWT token for authenticated requests
```

### Add Flashcard
```
POST /add-student
- Headers: Authorization: {token}
- Body: FormData with name, course, city, image
- Response: "Student added successfully"
- Description: Create new flashcard (Protected)
```

### Get All Flashcards
```
GET /students
- Response: [{ id, name, course, city, image }, ...]
- Description: Retrieve all flashcards
```

### Delete Flashcard
```
DELETE /delete/:id
- Headers: Authorization: {token}
- Params: id (flashcard ID)
- Response: "Deleted successfully"
- Description: Remove a flashcard (Protected)
```

## Authentication Details

The app uses JWT (JSON Web Tokens) for security:

- **Secret Key:** `secretkey` (Change in production!)
- **Token Expiry:** 1 hour
- **Protected Routes:** `/add-student`, `/delete/:id`

## Data Storage

Flashcards are stored in `students.json`:
```json
[
  {
    "id": 1234567890,
    "name": "Biology Basics",
    "course": "Biology",
    "city": "10th Grade",
    "image": "uploads/1234567890-biology.jpg"
  }
]
```

## Development Tips

### Adding New Features
1. Update API routes in `app.js`
2. Update frontend JavaScript in `index.html`
3. Test with Postman or browser console

### Debugging
- Check browser console (F12) for frontend errors
- Check terminal for backend errors
- Verify token is in localStorage
- Ensure uploads directory exists

### Security Improvements (Production)
1. Use environment variables for secret key
2. Implement password-based login
3. Use database instead of JSON file
4. Add input validation & sanitization
5. Implement HTTPS
6. Add rate limiting
7. Validate file types for uploads

## Common Issues

**Issue:** Uploads directory not found
```bash
mkdir uploads
```

**Issue:** Token expires
- Logout and login again

**Issue:** Cannot upload files
- Check uploads directory permissions
- Verify file size is reasonable

**Issue:** CORS errors
- Ensure CORS middleware is enabled (already done)

## Future Enhancements

- 🔄 Edit existing flashcards
- 🎯 Quiz mode to test knowledge
- 📊 Progress tracking
- 👥 User authentication with database
- 🏷️ Tagging system
- 🔍 Search functionality
- 📱 Mobile app version
- ☁️ Cloud storage for images

## License

ISC

## Author

Created for learning full-stack development

---

**Happy Learning! 📚**

For questions or issues, check the browser console or terminal output for error messages.