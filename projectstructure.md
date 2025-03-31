### **Project Structure**
```
tennis-club-booking/
├── backend/               # Go backend (REST API)
│   ├── cmd/
│   │   └── api/           # Main application entry point
│   │       └── main.go
│   ├── internal/
│   │   ├── handlers/      # HTTP request handlers
│   │   ├── models/        # Database models (e.g., User, Booking)
│   │   ├── services/      # Business logic (e.g., booking validation)
│   │   └── utils/         # Utilities (e.g., authentication, Stripe)
│   ├── migrations/        # Database migration scripts
│   ├── config/            # Configuration files (e.g., database.yml)
│   └── Dockerfile         # Dockerfile for Cloud Run
│
├── frontend/              # next.js frontend
    ├── app
    │   ├── favicon.ico
    │   ├── globals.css
    │   ├── layout.tsx
    │   └── page.tsx
    ├── next.config.ts
    ├── next-env.d.ts
    ├── package.json
    ├── package-lock.json
    ├── postcss.config.mjs
    ├── public
    │   ├── file.svg
    │   ├── globe.svg
    │   ├── next.svg
    │   ├── vercel.svg
    │   └── window.svg
    ├── README.md
    └── tsconfig.json
│
├── docker-compose.yml     # Local development setup (optional)
├── .github/               # GitHub Actions workflows
│   └── workflows/
│       └── ci-cd.yml
└── README.md
```

