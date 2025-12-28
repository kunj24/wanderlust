# 🌍 Wanderlust - Hotel Listing Platform

A modern, full-stack web application for discovering and managing hotel properties worldwide. Built with Node.js, Express.js, MongoDB Atlas, and EJS templating.

[![Live Demo](https://img.shields.io/badge/demo-live-brightgreen)](https://wanderlust-sylk.onrender.com)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

## ✨ Features

- 🔐 **User Authentication** - Secure signup, login, and logout with Passport.js
- 🏨 **Hotel Listings** - Browse, create, edit, and delete hotel listings
- ⭐ **Review System** - Rate and review hotels with star ratings and detailed comments
- 📱 **Responsive Design** - Beautiful mobile-friendly interface using Bootstrap 5
- 🖼️ **Image Management** - Support for external image URLs (Unsplash integration)
- 🔒 **Authorization** - Users can only modify their own listings and reviews
- ☁️ **Cloud Database** - MongoDB Atlas for reliable, scalable data storage
- 🚀 **Production Ready** - Deployed on Render with environment-based configuration

## 🛠️ Tech Stack

| Category | Technologies |
|----------|-------------|
| **Backend** | Node.js, Express.js |
| **Database** | MongoDB Atlas (Cloud), Mongoose ODM |
| **Authentication** | Passport.js (Local Strategy), bcrypt |
| **Session Management** | express-session, connect-flash |
| **Templating Engine** | EJS |
| **Frontend** | HTML5, CSS3, Bootstrap 5 |
| **Icons** | Font Awesome |
| **Deployment** | Render (Production) |
| **Version Control** | Git, GitHub |

## 📋 Prerequisites

- Node.js (v14 or higher)
- MongoDB Atlas account (or local MongoDB installation)
- npm or yarn package manager
- Git

## 🚀 Installation & Setup

### 1. Clone the Repository
```bash
git clone https://github.com/kunj24/wanderlust.git
cd wanderlust
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Environment Configuration
Create a `.env` file in the root directory with the following variables:
- `MONGODB_URI` - Your MongoDB Atlas connection string
- `SESSION_SECRET` - A strong secret key for session management
- `PORT` - Port number (optional, defaults to 8080)

**Note:** Never commit the `.env` file to version control. It's already in `.gitignore`.

### 4. Set Up MongoDB Atlas

1. Create a free account at [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Create a new cluster
3. Add a database user
4. Whitelist your IP address (or use `0.0.0.0/0` for development)
5. Get your connection string and add it to `.env`

### 5. Seed the Database
```bash
npm run seed
```
This creates:
- Default user (username: `demo`, password: `password123`)
- 29 sample hotel listings from around the world

### 6. Start the Application

**Development mode (with auto-restart):**
```bash
npm run dev
```

**Production mode:**
```bash
npm start
```

### 7. Access the Application
Open your browser and navigate to:
- Local: `http://localhost:3000`
- Production: `https://wanderlust-sylk.onrender.com`

## Project Structure

```
wunderlust/
├── models/              # Database models
│   ├── User.js         # User model with authentication
│   ├── Listing.js      # Hotel listing model
│   └── Review.js       # Review model
├── routes/              # Express routes
│   ├── listings.js     # Hotel listing CRUD operations
│   ├── reviews.js      # Review operations
│   └── users.js        # Authentication routes
├── views/               # EJS templates
│   ├── partials/       # Reusable components
│   │   ├── header.ejs  # Navigation and alerts
│   │   └── footer.ejs  # Footer with social links
│   ├── listings/       # Hotel listing-related views
│   │   ├── index.ejs   # All hotel listings grid
│   │   ├── show.ejs    # Single hotel listing details
│   │   ├── new.ejs     # Create hotel listing form
│   │   └── edit.ejs    # Edit hotel listing form
│   └── users/          # User authentication views
│       ├── signup.ejs  # Registration form
│       └── login.ejs   # Login form
├── public/              # Static assets
│   └── css/            # Custom stylesheets
│       └── style.css   # Main CSS file
├── server.js            # Express server entry point
├── seed.js              # Database seeding script
├── sampleListings.js    # Sample hotel data for seeding
├── middleware.js        # Authentication middleware
├── package.json         # Project dependencies
└── README.md            # This file
```

## API Endpoints

### Authentication
- `GET /signup` - Show signup form
- `POST /signup` - Create new user account
- `GET /login` - Show login form
- `POST /login` - Authenticate user
- `GET /logout` - Logout user

### Listings
- `GET /listings` - Show all hotel listings
- `GET /listings/new` - Show create hotel listing form (authenticated)
- `POST /listings` - Create new hotel listing (authenticated)
- `GET /listings/:id` - Show specific hotel listing
- `GET /listings/:id/edit` - Show edit form (owner only)
- `PUT /listings/:id` - Update hotel listing (owner only)
- `DELETE /listings/:id` - Delete hotel listing (owner only)

### Reviews
- `POST /reviews/:id` - Add review to hotel listing (authenticated)
- `DELETE /reviews/:id` - Delete review (author only)

## Default User Credentials

After running the seed script, you can login with:
- **Username**: `demo`
- **Password**: `password123`

## Features in Detail

### Hotel Listings
- Grid layout displaying hotel images, titles, prices, and locations
- Responsive design that works on all device sizes
- Each hotel listing card shows key information and links to detailed view

### Hotel Listing Management
- Authenticated users can create new hotel listings
- Hotel owners can edit and delete their listings
- Form validation ensures data integrity

### Review System
- Star rating system (1-5 stars)
- Comment functionality for detailed feedback
- Users can only delete their own reviews
- Reviews are displayed on hotel listing detail pages

### User Experience
- Flash messages for success/error feedback
- Responsive navigation with user authentication status
- Clean, modern UI using Bootstrap components
- Smooth animations and hover effects

## Customization

### Adding New Fields
To add new fields to hotel listings (e.g., amenities, pet-friendly status):
1. Update the `Listing` model in `models/Listing.js`
2. Modify the forms in `views/listings/new.ejs` and `views/listings/edit.ejs`
3. Update the display templates as needed

### Styling Changes
- Main styles are in `public/css/style.css`
- Bootstrap classes provide responsive layout and components
- Custom CSS adds animations and specific styling

### Database Schema
The application uses three main collections:
- **Users**: Authentication and user management
- **Listings**: Hotel information and metadata
- **Reviews**: User feedback and ratings


## 📁 Project Structure

```
wanderlust/
├── models/              # Mongoose database models
│   ├── User.js         # User schema with bcrypt authentication
│   ├── Listing.js      # Hotel listing schema
│   └── Review.js       # Review schema with references
├── routes/              # Express route handlers
│   ├── listings.js     # Hotel listing CRUD operations
│   ├── reviews.js      # Review management
│   └── users.js        # Authentication routes
├── views/               # EJS templates
│   ├── partials/       # Reusable components
│   │   ├── header.ejs  # Navigation bar with auth status
│   │   └── footer.ejs  # Footer with social links
│   ├── listings/       # Hotel listing views
│   │   ├── index.ejs   # Grid view of all hotels
│   │   ├── show.ejs    # Detailed hotel page with reviews
│   │   ├── new.ejs     # Create listing form
│   │   └── edit.ejs    # Edit listing form
│   ├── users/          # Authentication views
│   │   ├── signup.ejs  # User registration
│   │   └── login.ejs   # User login
│   └── error.ejs       # Error page
├── public/              # Static assets
│   └── css/
│       └── style.css   # Custom styles and animations
├── server.js            # Main Express application
├── seed.js              # Database seeding script
├── sampleListings.js    # Sample hotel data
├── middleware.js        # Custom middleware (auth checks)
├── .env                 # Environment variables (not in repo)
├── .gitignore          # Git ignore rules
├── package.json         # Dependencies and scripts
└── README.md            # This file
```

## 🌐 API Endpoints

### 🔐 Authentication Routes
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/signup` | Show signup form | No |
| POST | `/signup` | Create new user account | No |
| GET | `/login` | Show login form | No |
| POST | `/login` | Authenticate user | No |
| GET | `/logout` | Logout current user | Yes |

### 🏨 Listing Routes
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/listings` | Show all hotel listings | No |
| GET | `/listings/new` | Show create listing form | Yes |
| POST | `/listings` | Create new listing | Yes |
| GET | `/listings/:id` | Show specific listing | No |
| GET | `/listings/:id/edit` | Show edit form | Yes (Owner) |
| PUT | `/listings/:id` | Update listing | Yes (Owner) |
| DELETE | `/listings/:id` | Delete listing | Yes (Owner) |

### ⭐ Review Routes
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/reviews/:id` | Add review to listing | Yes |
| DELETE | `/reviews/:id` | Delete review | Yes (Author) |

## 👤 Default User Credentials

After seeding the database:
```
Username: demo
Password: password123
```

## 💡 Key Features Explained

### 🏨 Hotel Listings
- **Grid Layout** - Responsive card-based design
- **Search & Filter** - Browse hotels by location, price
- **Detailed View** - Comprehensive hotel information
- **CRUD Operations** - Full create, read, update, delete
- **Owner Protection** - Only owners can modify their listings

### ⭐ Review System
- **Star Ratings** - 1-5 star rating system
- **Comments** - Detailed text feedback
- **User Attribution** - Reviews linked to accounts
- **Delete Protection** - Users can only delete their own reviews
- **Integration** - Reviews displayed on listing pages

### 🔒 Security Features
- **Password Hashing** - bcrypt with salt rounds
- **Session Management** - Secure session configuration
- **Authentication Middleware** - Protected routes
- **Authorization Checks** - Owner/author verification
- **Environment Variables** - Sensitive data protection
- **CSRF Protection** - Method override for safe operations

## 🚀 Deployment

### Deploy to Render

1. **Push to GitHub**
   ```bash
   git add .
   git commit -m "Ready for deployment"
   git push origin main
   ```

2. **Configure Render**
   - Sign up at [Render](https://render.com)
   - Create new Web Service
   - Connect GitHub repository
   - Build command: `npm install`
   - Start command: `npm start`

3. **Add Environment Variables in Render Dashboard**
   - `MONGODB_URI` - Your MongoDB Atlas connection string
   - `SESSION_SECRET` - Strong random secret for production
   - `NODE_ENV` - Set to `production`

4. **Whitelist IP in MongoDB Atlas**
   - Network Access → Add IP: `0.0.0.0/0`

5. **Deploy** - Automatic deployment

**Live Demo:** [https://wanderlust-sylk.onrender.com](https://wanderlust-sylk.onrender.com)

## 🔧 Development

### Commands
```bash
npm install       # Install dependencies
npm run dev       # Development with auto-restart
npm start         # Production mode
npm run seed      # Seed database
```

### Debugging
- Check terminal for server errors
- Browser console for client errors
- MongoDB Atlas dashboard for database logs
- MongoDB Compass for GUI database management

## ⚠️ Troubleshooting

### Common Issues

**MongoDB Connection Error**
```
Solution:
- Verify MongoDB Atlas connection string in .env
- Check IP whitelist in MongoDB Atlas (Network Access)
- Ensure database user credentials are correct
```

**Port Already in Use**
```
Solution:
- Change PORT in .env file
- Kill process: npx kill-port 3000 (Windows/Mac/Linux)
```

**Authentication Issues**
```
Solution:
- Clear browser cookies
- Verify user exists in database
- Check SESSION_SECRET is set in .env
```

**Deployment Fails on Render**
```
Solution:
- Add environment variables in Render dashboard
- Whitelist 0.0.0.0/0 in MongoDB Atlas
- Check build logs for specific errors
```

**Images Not Loading**
```
Solution:
- Verify image URLs are accessible
- Check browser console for CORS errors
- Use HTTPS URLs for production
```

## 🎨 Customization

### Add New Listing Fields
1. Update schema in `models/Listing.js`
2. Modify forms in `views/listings/new.ejs` and `edit.ejs`
3. Update display in `views/listings/show.ejs`

### Change Styling
- Edit `public/css/style.css` for custom styles
- Bootstrap classes in EJS templates
- Add new CSS files in `public/css/`

### Database Schema
```javascript
Users Collection:
- username (String, unique)
- email (String, unique)
- password (String, hashed)

Listings Collection:
- title, description, location, country
- price (Number)
- image {filename, url}
- owner (ref: User)

Reviews Collection:
- rating (Number, 1-5)
- comment (String)
- author (ref: User)
- listing (ref: Listing)
```

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Make your changes and commit: `git commit -m 'Add feature'`
4. Push to branch: `git push origin feature-name`
5. Submit a pull request

## 📝 Future Enhancements

- [ ] Search and filter functionality
- [ ] Map integration for hotel locations
- [ ] Image upload with Cloudinary
- [ ] Email verification for users
- [ ] Password reset functionality
- [ ] Admin dashboard
- [ ] Booking system
- [ ] Payment integration
- [ ] Multi-language support
- [ ] Advanced filters (price range, amenities)

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Kunj**
- GitHub: [@kunj24](https://github.com/kunj24)
- Project Link: [https://github.com/kunj24/wanderlust](https://github.com/kunj24/wanderlust)
- Live Demo: [https://wanderlust-sylk.onrender.com](https://wanderlust-sylk.onrender.com)

## 🙏 Acknowledgments

- [Unsplash](https://unsplash.com) for beautiful hotel images
- [Bootstrap](https://getbootstrap.com) for responsive UI components
- [Font Awesome](https://fontawesome.com) for icons
- [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) for cloud database hosting
- [Render](https://render.com) for deployment platform

## 📞 Support

For support, questions, or feedback:
- Open an issue on [GitHub](https://github.com/kunj24/wanderlust/issues)
- Email: [Your Email]
- Star ⭐ this repository if you find it helpful!

---

**Made with ❤️ by Kunj**

