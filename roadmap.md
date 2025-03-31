# Booking System Roadmap

## **Project Requirements**
1. **User Roles**:
   - **Admin**: Manage courts, view all bookings, add/remove users.
   - **Member**: Book courts, view/edit/delete their own bookings.
   - **Guest**: View court availability (no booking without registration).

2. **Booking Features**:
   - Time slots with restrictions:
     - Max booking duration (e.g., 2 hours).
     - Advance booking limit (e.g., up to 7 days in advance).
   - No recurring bookings.

3. **Payment**:
   - **Stripe** for pay-per-booking payments.
   - No membership plans.

4. **Notifications**:
   - Email/SMS for booking confirmations, reminders (1 day before), and cancellations.

5. **Scalability**:
   - Initial 200 users, 5% annual growth (low traffic; optimize for cost and simplicity).

6. **Authentication**:
   - **Google OAuth** for user registration/login (simplifies onboarding and security).

7. **Deployment**:
   - **GCP Recommendations**:
     - **Backend**: Cloud Run (serverless, auto-scaling, cost-effective).
     - **Database**: Cloud SQL (managed PostgreSQL).
     - **Frontend**: Firebase Hosting (fast, secure, integrates with Google OAuth).
   - **CI/CD**: GitHub Actions (easy to set up, integrates with GitHub repos).

---

### **Project Roadmap**

#### **Phase 1: Planning and Setup**
1. **Finalize Requirements**:
   - ~~Define booking restrictions (e.g., max 2-hour slots, 7-day advance limit).~~
   - notification service will be **SendGrid** for email, **Twilio** for SMS.

2. **Set Up Development Environment**:
   - ~~Go, PostgreSQL, React.js, and Stripe CLI for local testing.~~
   - ~~Create a GitHub repository.~~

3. **Database Schema**: (moved to its own md file)

---

#### **Phase 2: Backend Development**
1. **Authentication**:
   - Implement Google OAuth using the `golang.org/x/oauth2` package.
   - Secure API endpoints with JWT middleware for role-based access.

2. **Booking Logic**:
   - Validate time slots (no overlaps, max duration, advance limits).
   - Integrate Stripe for payment processing (create charges, handle webhooks).

3. **Admin Features**:
   - CRUD for courts (name, description, availability).
   - User management (promote/demote admins, delete users).

4. **Notifications**:
   - Trigger emails/SMS via SendGrid/Twilio on booking/cancellation.

---

#### **Phase 3: Frontend Development**
1. **Authentication Flow**:
   - Google OAuth login/register button using `react-google-login`.
   - Redirect unauthenticated users to login.

2. **Booking Interface**:
   - Calendar component (e.g., `react-big-calendar`) to display court availability.
   - Payment form integrated with Stripe.js.

3. **Admin Panel**:
   - Dashboard to manage courts and view all bookings.

---

#### **Phase 4: Testing**
1. **Stripe Testing**:
   - Use Stripe test mode and mock webhooks.

2. **End-to-End Testing**:
   - Test booking flow, payment failures, and notifications.

---

#### **Phase 5: Deployment**
1. **GCP Setup**:
   - **Cloud SQL**: Create a PostgreSQL instance.
   - **Cloud Run**: Deploy the Go backend (containerized with Docker).
   - **Firebase Hosting**: Deploy the React frontend.

2. **CI/CD Pipeline**:
   - GitHub Actions workflow to:
     - Run tests on PRs.
     - Build Docker images for Cloud Run.
     - Deploy frontend to Firebase.

3. **Monitoring**:
   - Enable Cloud Run logging and Firebase performance monitoring.

---

### **Best Practices**
1. **Security**:
   - Store Stripe API keys and OAuth secrets in GCP Secret Manager.
   - Use HTTPS everywhere (Cloud Run and Firebase enforce this by default).

2. **Cost Optimization**:
   - Use Cloud Run’s pay-per-use pricing (scales to zero).
   - Set up budget alerts in GCP.

3. **Notifications**:
   - Use **SendGrid** for email (free tier supports 100 emails/day).
   - Use **Twilio** for SMS (low-cost pay-as-you-go).

---

### **Next Steps**
1. Start with **Phase 1**: Set up the GitHub repo and define the database schema.
2. Proceed to **Phase 2**: Begin backend development with authentication and booking logic.
