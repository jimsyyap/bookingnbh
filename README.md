```markdown
# Tennis Club Booking System

An online booking system for a local tennis club built with Go, React, PostgreSQL, and Stripe. Deployed on Google Cloud Platform.

## Features
- **User Roles**: Admin, Member, Guest.
- **Booking**: Time slots with max duration and advance limits.
- **Payments**: Pay-per-booking via Stripe.
- **Notifications**: Email/SMS confirmations and reminders.
- **Authentication**: Google OAuth + JWT.

## Tech Stack
- **Backend**: Go (Gin, GORM, Stripe SDK)
- **Frontend**: React.js (Axios, React Router)
- **Database**: PostgreSQL
- **Deployment**: GCP (Cloud Run, Cloud SQL, Firebase)
- **CI/CD**: GitHub Actions

## Setup

### Prerequisites
- Go 1.20+
- Node.js 18+
- Docker (for local PostgreSQL)
- Google Cloud Account

### Backend
1. **Environment Variables**:
   ```bash
   # .env (backend)
   PORT=8080
   DB_URL=postgres://user:pass@localhost:5432/tennis_club
   STRIPE_SECRET_KEY=sk_test_...
   GOOGLE_CLIENT_ID=...
   GOOGLE_CLIENT_SECRET=...
   ```

2. **Run Migrations**:
   ```bash
   go run cmd/migrate/main.go
   ```

3. **Start Server**:
   ```bash
   go run cmd/api/main.go
   ```

### Frontend
1. **Environment Variables**:
   ```bash
   # .env (frontend)
   REACT_APP_API_URL=http://localhost:8080
   REACT_APP_STRIPE_PUBLIC_KEY=pk_test_...
   ```

2. **Start Dev Server**:
   ```bash
   cd frontend
   npm install && npm start
   ```

### Testing
- **Backend Tests**:
  ```bash
  go test ./...
  ```

- **Frontend Tests**:
  ```bash
  npm test
  ```

## Deployment

### Google Cloud
1. **Build Docker Images**:
   ```bash
   # Backend
   docker build -t gcr.io/your-project/backend .
   docker push gcr.io/your-project/backend

   # Frontend
   docker build -t gcr.io/your-project/frontend -f frontend/Dockerfile .
   docker push gcr.io/your-project/frontend
   ```

2. **Deploy to Cloud Run**:
   ```bash
   gcloud run deploy backend --image gcr.io/your-project/backend --platform managed
   ```

3. **Deploy Frontend to Firebase**:
   ```bash
   firebase deploy --only hosting
   ```

## CI/CD
- Push changes to GitHub to trigger the workflow:
  ```bash
  git push origin main
  ```

## Contributing
Pull requests are welcome! For major changes, please open an issue first.

## License
MIT
```

