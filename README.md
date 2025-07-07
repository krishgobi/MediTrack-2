# 🏥 MediTrack - Medical History Management System

A comprehensive Flask-based web application for managing medical histories, patient records, reminders, and documentation in healthcare settings.

## ✨ Features

### 📊 Dashboard
- Modern, responsive dashboard with real-time statistics
- Quick access to subjects, patients, reminders, and upcoming exams
- Interactive chatbot for quick queries
- Profile management with persistent name changes

### 👨‍⚕️ Subject Management
- Add, view, edit, and delete medical subjects
- Staff assignment and note-taking capabilities
- Subject history tracking
- Comprehensive subject details view

### 🏥 Patient Records
- Detailed patient history management
- Disease tracking and documentation
- Medical posting assignments
- Duration and reminder scheduling
- Extra fields for additional information (JSON format)

### 🔔 Smart Reminders
- Email notifications with customizable timing
- Automatic PDF generation for medical records
- File attachments support
- Background scheduling with APScheduler
- Timezone-aware reminders (Asia/Kolkata)

### 📅 Exam Scheduling
- Exam date and time management
- Automated reminder notifications
- Subject-wise exam organization
- Email alerts with attachments

### 📄 Document Management
- File upload and organization
- Multiple file format support
- Recycle bin functionality
- Subject-specific file categorization
- Bulk PDF download capabilities

### 🤖 AI-Powered Chatbot
- Integrated Gemini AI for intelligent responses
- Database-first query processing
- Medical context awareness
- Quick access to patient records, subjects, and reminders
- Direct links to relevant pages

### 📱 Mobile-Responsive Design
- Modern Bootstrap 5 UI
- Responsive navigation bar
- Mobile-optimized interface
- Progressive enhancement

## 🚀 Quick Start

### Prerequisites
- Python 3.8 or higher
- pip (Python package installer)

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd MedicoApp
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up environment variables** (optional)
   Create a `.env` file in the root directory:
   ```env
   FLASK_ENV=development
   SECRET_KEY=your-secret-key
   GEMINI_API_KEY=your-gemini-api-key
   SMTP_USERNAME=your-email@gmail.com
   SMTP_PASSWORD=your-app-password
   ```

4. **Initialize the database**
   ```bash
   python app.py
   ```
   The SQLite database will be created automatically on first run.

5. **Run the application**
   ```bash
   python app.py
   ```
   Visit `http://localhost:5000` in your browser.

## 🔧 Configuration

### Email Settings
Configure SMTP settings in `app.py`:
```python
SMTP_SERVER = "smtp.gmail.com"
SMTP_PORT = 587
SMTP_USERNAME = "your-email@gmail.com"
SMTP_PASSWORD = "your-app-password"
```

### Gemini AI Integration
Add your Gemini API key:
```python
GEMINI_API_KEY = "your-gemini-api-key"
```

### File Upload Configuration
Customize upload directories:
```python
UPLOAD_FOLDER = 'uploads'
STORAGE_FOLDER = 'user_uploads'
```

## 📊 Database Schema

### Core Models
- **UserAuthentication**: User management and profile data
- **SubjectHistory**: Patient medical records and histories
- **Subject**: Medical subjects and staff assignments
- **Remainder**: Scheduled reminders and notifications
- **Exam**: Exam scheduling and management
- **FileMeta**: Document metadata and organization
- **Conversation**: Chatbot interaction history

### Database Features
- SQLite for development (easily configurable for PostgreSQL/MySQL)
- Automatic migrations with Flask-Migrate
- JSON field support for flexible data storage
- Foreign key relationships for data integrity

## 🏗️ Project Structure

```
MedicoApp/
├── app.py                      # Main Flask application
├── requirements.txt            # Python dependencies
├── README.md                  # Project documentation
├── subjects_data.json         # Subject storage file
├── instance/
│   ├── newdata.db            # SQLite database
│   └── ...
├── templates/                 # HTML templates
│   ├── base.html             # Base template with navbar
│   ├── dashboard.html        # Main dashboard
│   ├── subject_history.html  # Subject history view
│   ├── view_subject.html     # Subject management
│   └── ...
├── static/                    # CSS, JS, and static assets
│   ├── style.css
│   ├── modern.css
│   └── ...
├── uploads/                   # User uploaded files
├── uplo/                     # Additional upload directory
└── user_uploads/             # User-specific uploads
```

## 🚀 Deployment

### Production with Gunicorn
```bash
gunicorn --bind 0.0.0.0:8000 app:app
```

### Docker Deployment (optional)
```dockerfile
FROM python:3.9-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
EXPOSE 5000
CMD ["gunicorn", "--bind", "0.0.0.0:5000", "app:app"]
```

### Environment Variables for Production
```env
FLASK_ENV=production
SECRET_KEY=your-production-secret-key
DATABASE_URL=your-database-url
SMTP_USERNAME=your-production-email
SMTP_PASSWORD=your-production-password
GEMINI_API_KEY=your-production-api-key
```

## 🔒 Security Features

- **Password Hashing**: Bcrypt for secure password storage
- **Session Management**: Flask session handling
- **File Security**: Secure filename handling with Werkzeug
- **Input Validation**: Form validation and sanitization
- **CSRF Protection**: Built-in Flask security features

## 📧 Email Notifications

### Features
- Automated email reminders
- PDF attachment generation
- Medical record summaries
- Exam notifications
- Customizable email templates

### Setup Gmail SMTP
1. Enable 2-factor authentication
2. Generate an app-specific password
3. Update SMTP credentials in the configuration

## 🤖 AI Chatbot Features

### Database Integration
- Real-time query processing
- Medical context understanding
- Subject and patient search
- Reminder and exam queries

### Gemini AI Fallback
- Natural language processing
- Medical knowledge base
- Contextual responses
- Error handling

## 🛠️ Development

### Running in Development Mode
```bash
export FLASK_ENV=development
python app.py
```

### Database Migrations
```bash
flask db init
flask db migrate -m "Migration message"
flask db upgrade
```

### Adding New Features
1. Define models in the Models section
2. Create routes in the Routes section
3. Add templates in the templates/ directory
4. Update the navbar in base.html
5. Test thoroughly

## 📱 API Endpoints

### Core Routes
- `GET /` - Dashboard
- `GET /dashboard` - Dashboard (alternative)
- `GET /view_subject` - Subject management
- `GET /subject_history_page` - Patient history
- `GET /view_remainders` - Reminders view
- `GET /documents` - Document management

### API Routes
- `POST /chatbot_ask` - Chatbot queries
- `POST /rename_profile` - Profile updates
- `POST /add_subject` - Add new subject
- `POST /add_history` - Add patient history
- `POST /add_remainder` - Add reminder
- `POST /add_exam` - Schedule exam

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🆘 Support

For support and questions:
- Create an issue in the repository
- Check the documentation
- Review the code comments

## 🔄 Version History

### v1.0.0 (Current)
- Full medical history management
- AI-powered chatbot integration
- Email notification system
- Responsive design
- Document management
- Exam scheduling
- Profile management with database persistence

## 🙏 Acknowledgments

- Flask community for the excellent framework
- Bootstrap for the responsive UI components
- Google Gemini AI for chatbot capabilities
- ReportLab for PDF generation
- APScheduler for background task management

---

**MediTrack** - Streamlining healthcare documentation and patient management. 🏥✨
