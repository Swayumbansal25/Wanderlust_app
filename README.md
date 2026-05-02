Wanderlust 🌍
A full-stack property listing web application inspired by Airbnb, built from scratch using Node.js, Express.js, and MongoDB. Users can browse listings, create their own properties with image uploads, and manage their accounts through a fully authenticated system.

🚀 Live Features

User Authentication — Secure Register and Login system with session-based auth and protected routes
Property Listings — Create, read, update, and delete property listings with title, description, price, location, and images
Image Uploads — Real file upload support via Cloudinary — images are stored in the cloud, not locally
Reviews System — Authenticated users can leave reviews on listings; only the review author can delete their own
Authorization — Users can only edit or delete their own listings and reviews — no unauthorised access
Responsive UI — Clean, mobile-friendly interface built with EJS templates and CSS3
Flash Messages — User-friendly success and error notifications on all key actions
Input Validation — Server-side validation via Joi schema before any data hits the database


🛠️ Tech Stack
Layer            Technology
Runtime           Node.js 
Framework         Express.js
Templating        EJS (Embedded JavaScript)
Database          MongoDB with Mongoose ODM
Authentication    Passport.js (Local Strategy) + express-session
Image Storage     Cloudinary + Multer
Validation        Joi
Styling           CSS3
Architecture      MVC (Model-View-Controller)

📁 Project Structure
Wanderlust_app/
├── controllers/        # Route handler logic (listings, reviews, users)
├── models/             # Mongoose schemas (Listing, Review, User)
├── routes/             # Express route definitions
├── views/              # EJS templates
│   ├── listings/       # Index, show, new, edit pages
│   ├── users/          # Login and register pages
│   └── partials/       # Navbar, footer, flash messages
├── public/             # Static assets (CSS, JS, images)
├── utils/              # ExpressError class and async wrapper
├── middleware.js        # Auth checks and validation middleware
├── cloudConfig.js      # Cloudinary + Multer configuration
├── init/               # Database seed data
├── schema.js           # Joi validation schemas
└── app.js              # Express app entry point

⚙️ Getting Started
Prerequisites

Node.js (v18+)
MongoDB (local or MongoDB Atlas)
Cloudinary account (free tier works)

1. Clone the Repository
bashgit clone https://github.com/Swayumbansal25/Wanderlust_app.git
cd Wanderlust_app
2. Install Dependencies
bashnpm install
3. Set Up Environment Variables
Create a .env file in the root directory:
envATLASDB_URL=your_mongodb_connection_string
SECRET=your_session_secret_key
CLOUD_NAME=your_cloudinary_cloud_name
CLOUD_API_KEY=your_cloudinary_api_key
CLOUD_API_SECRET=your_cloudinary_api_secret
4. Seed the Database (Optional)
bashnode init/index.js
5. Start the Server
bashnode app.js
Visit http://localhost:8080 in your browser.

🏗️ Architecture — MVC Pattern
This project strictly follows the Model-View-Controller pattern:

Models (/models) — Mongoose schemas define the data structure for Listings, Reviews, and Users. Relationships are handled via MongoDB references.
Views (/views) — EJS templates render server-side HTML. Partials keep the navbar, footer, and flash messages DRY.
Controllers (/controllers) — All business logic lives here, cleanly separated from route definitions. Routes simply point to the right controller method.
Middleware (middleware.js) — Custom middleware handles authentication checks (isLoggedIn), ownership checks (isOwner, isReviewAuthor), and Joi validation — all before the controller is ever reached.


🔐 Authentication & Authorization

Sessions managed with express-session and stored in MongoDB via connect-mongo
Passport.js Local Strategy handles login with hashed passwords (passport-local-mongoose)
Protected routes redirect unauthenticated users to the login page with a flash message
Ownership middleware ensures users can only modify their own listings and reviews

☁️ Image Upload Flow

User submits a listing form with an image file
Multer intercepts the multipart form data before it reaches the controller
Cloudinary receives the file via the configured storage engine (cloudinary.multer)
Cloudinary returns a secure URL and public ID, which are saved to MongoDB

🙋‍♂️ Author
Swayum Bansal
GitHub: @Swayumbansal25
LinkedIn: swayum-bansal-2aa254377
LinkedIn: swayum-bansal-2aa254377
GitHub: @Swayumbansal25
LinkedIn: swayum-bansal-2aa254377
