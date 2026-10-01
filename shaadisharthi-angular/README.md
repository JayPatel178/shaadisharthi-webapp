# ShaadiSharthi – Service Provider Portal

This repository contains the **Service Provider Frontend** of the **ShaadiSharthi** wedding services platform, built with Angular and Bootstrap.
It allows service providers (e.g., photographers, caterers, decorators) to register, manage their business, upload services with media, and handle bookings—all connected to a Java Servlet backend.

> ⚠️ Note: This repo only contains the **Service Provider Frontend** (Angular + Bootstrap).  
> The platform also has:  
> - **Admin frontend** (github.com/JayPatel178/shaadisharthi-admin)  
> - **Customer frontend** (github.com/JayPatel178/shaadisharthi-customer)  
> - **Java Backend** (github.com/JayPatel178/shaadisharthi-backend, built with Servlets)  


---

## Live demo & repos
- **Live Demo URL**: `https://shaadisharthi.theworkpc.com/provider`

---

## 🚀 Tech Stack

- **Frontend Framework**: [Angular](https://angular.io/)
- **Styling**: [Bootstrap](https://getbootstrap.com/)
- **Backend**: Java (Servlets, REST APIs)
- **Database**: MySQL
- **Authentication**: JWT (stored in Local Storage)
- **Media Storage**: [Cloudinary](https://cloudinary.com/) (via signed uploads)
- **Charts**: Angular chart libraries

---

## 🎯 Features

### 🔐 Authentication & Onboarding
- **Login/Signup** flow with JWT-based authentication.
- **Forgot Password** → Email-based reset link with a one-time JWT.
- **Create Account** → Email-based flow to set password, name, and email.
- **Role-based Redirection**:
  - `Basic Registered` → Redirected to Business Details form.
  - `Pending Approval` → Redirected to a waiting page.
  - `Approved` → Full access to the dashboard.

### 📝 Business Registration & Approval
- **Business Details Form** where providers submit:
  - Business name, GST, Aadhaar, PAN, location, and phone numbers.
- **Admin Approval System**:
  - Admin reviews submitted details.
  - Provider receives an email notification on approval or rejection (with reason).

### 📊 Dashboard
- **Personalized Dashboard** with widgets for:
  - Upcoming orders, total bookings, and customer stats.
- **Graphs & Charts** for booking analysis:
  - Status breakdown (Pending / Accepted / Rejected / Completed).
  - Service performance and ratings.
  - Financial overview.
- **Sidebar Navigation** for easy access to all features.

### 🛠️ Service Management
- **CRUD Operations** for services (Add/Edit/Delete).
  - Define service name, category, description, and price.
- **Media Uploads** for images and videos.
- **Cloudinary Integration**:
  - Backend generates a signature for direct, secure uploads from the client.
  - Media metadata is stored in the backend database.
- **Caching**: Service data is cached on the client to reduce backend calls.

### 📅 Booking Management
- **Pending Bookings**:
  - View a list of new customer bookings.
  - `Accept` or `Reject` bookings (with an optional reason for rejection).
- **Confirmed Bookings**:
  - View all accepted bookings with customer and service details.
  - `Mark as Complete` (only after the event date).
  - `Cancel` a confirmed booking.
- **Performance Scaling** for large lists:
  - **Virtual Scrolling (Angular CDK)** renders only visible items in the DOM, ensuring smooth performance even with hundreds of bookings.
  - **Hybrid Infinite Scroll + Pagination** fetches bookings in chunks (20 at a time) as the user scrolls.

### 👤 Account & Support
- **Profile Management**:
  - View and edit personal and business details (name, address, contact info).
- **Document Management**:
  - Upload and view legal documents (GST, Aadhaar, PAN).
- **Change Password** with current and new password validation.
- **FAQs Page** with an expandable Q&A list managed by the admin.
- **Contact Support** form to submit queries directly to the admin.

### 🛡️ Security
- **Current State**:
  - JWT stored in `localStorage` (vulnerable to XSS).
  - Role-based route guards for different provider statuses.
- **Planned Improvements**:
  - Migrate JWT to HttpOnly cookies for enhanced security.
  - Implement stricter token expiry and refresh logic.

### ⚡ Performance Optimizations
- **Client-Side Caching** of service data.
- **Lazy Loading** for the services module.
- **Virtual Scrolling** and **Infinite Scroll** for booking lists.

---

## ⚙️ Getting Started

### 1. Clone the repo
```bash
git clone https://github.com/your-username/shaadisharthi-provider.git
cd shaadisharthi-provider
```

### 2. Install dependencies
```bash
npm install
```

### 3. Set up environment variables
Create a file `src/environments/environment.ts` with the following content:
```typescript
export const environment = {
  production: false,
  apiUrl: 'http://localhost:8080/ShaadiSharthi',
  cloudinary: {
    cloudName: 'YOUR_CLOUD_NAME',
  },
  supportEmail: 'support@shaadisharthi.com'
};
```

### 4. Run development server
```bash
ng serve
```
Navigate to `http://localhost:4200/provider`. The app will automatically reload if you change any of the source files.

---

## 📈 Future Roadmap

- **Security Hardening**: Migrate from `localStorage` to HttpOnly cookies and implement a stricter token refresh flow.
- **Cloudinary Cleanup**: Automate the removal of unused media from Cloudinary via a scheduled service.
- **Multi-language Support**: Expand the UI to support multiple languages.
- **Robust Media Uploading**: Add file size limits, better error handling, and MIME type validation.
- **Real-time Notifications**: Use WebSockets for instant booking updates.
- **Advanced Analytics**: Introduce trends, financial forecasting, and customer retention insights.

---

## 👨‍💻 Contact

-   **Author**: JAY PATEL — Full Stack Developer (Java + Modern JS Frameworks)
-   **Email**: jayptl565188@example.com
-   **GitHub**: github.com/JayPatel178

---

## 📜 License

-   This repository is provided for portfolio and educational purposes.

---
Built with ❤️ for the wedding industry

