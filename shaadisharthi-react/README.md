# ShaadiSharthi – Admin Panel Frontend

This repository contains the **Admin Panel frontend** for the **ShaadiSharthi** wedding services platform. Administrators use this panel to manage users, oversee platform activity, and handle support queries.

> ⚠️ Note: This repo only contains the **Admin Frontend** (React + Bootstrap).  
> The platform also has:  
> - **Customer frontend** (github.com/JayPatel1785651/shaadisharthi-customer)  
> - **Service Provider frontend** (github.com/JayPatel1785651/shaadisharthi-provider)  
> - **Java Backend** (github.com/JayPatel1785651/shaadisharthi-backend, built with Servlets)

---

## Live demo & repos
- **Live Demo URL**: `https://shaadisharthi.theworkpc.com/admin`

---

## 🚀 Tech Stack

- **Framework**: [React](https://reactjs.org/)
- **Styling**: [Bootstrap](https://getbootstrap.com/)
- **Backend**: Java (Servlets, Tomcat, JDBC)
- **Database**: MySQL
- **Auth**: JWT, TOTP (Time-based One-Time Password), Role-Based Access Control (RBAC)

---

## 🎯 Features

### 🔐 Authentication & Security

#### Admin Login Flow
- **Secure URL**: Admins access the panel via a dedicated, non-public URL.
- **Login Form**: Requires Email, Password, and a 6-digit TOTP.
- **First-Time Login**:
  - System generates a QR code for admins to set up TOTP in an authenticator app (e.g., Google Authenticator).
  - After setup, the admin is redirected to the login page.
- **Normal Login**: Authenticates using email, password, and the current TOTP code.

#### Progressive Lockout (Anti-Brute-Force)
- **3 failed attempts** → lock for 28 seconds.
- **4 failed attempts** → lock for 117 seconds.
- **5 failed attempts** → lock for 1 hour.

#### Two-Factor Authentication (TOTP)
- A 6-digit code that rotates every 30 seconds ensures secure access.

#### Role-Based Access Control (RBAC)
- Supports 3–4 distinct admin roles with different permissions.
- Each API request is verified with a JWT to check the admin's role and grant or deny access.
- Unauthorized attempts result in an “Insufficient Role Privileges” error.

### 🖥️ Dashboard
- **Header**: Displays Admin Name, Account Settings/Profile link, and a Sign Out button.
- **Sidebar**: Navigation links are dynamically rendered based on the admin's role permissions.
- **Widgets & Charts**:
  - Total Customers & Service Providers.
  - User registration trends (year-over-year).
  - Order volume comparison (current vs. previous year).
  - Service category distribution pie chart.

### 👤 My Profile
- View and edit personal details: Full Name, Phone Number, Email, and Address.
- Change password (requires entering the current password for verification).

### 📂 Customer Management
- **Customer List**: A paginated table showing Customer ID, Name, Registration Date, and Actions.
- **Actions**:
  - **View**: Modal displays full customer details.
  - **Edit**: Modify customer information like phone and address.
  - **Delete**: Remove a customer from the platform.
- **Search**: Filter customers by ID, Name, Phone, or Email.

### 🏢 Service Provider Management
- **Provider List**: A paginated table showing Provider Name, Registration Date, Status, and Actions.
- **Status Types**:
  - `Basic Registered`: Signed up with email and password only.
  - `Pending Approval`: Submitted business details and awaiting admin verification.
  - `Approved`: Verified and active on the platform.
- **Actions**:
  - **View**: Modal displays full provider details, including business info (GST, Aadhaar, PAN).
  - **Edit/Delete**: Manage provider accounts.
- **Approval Workflow**:
  - Admins can filter to see only providers with `Pending Approval` status.
  - **Approve**: Updates status and sends an approval email notification.
  - **Reject**: Requires a reason for rejection, which is included in a notification email.
- **Search**: Filter providers by Name, Email, or Phone.

### 📨 Query Management
- **Query Queue**: A table lists user queries with status (Pending/Resolved), assigned admin, and other details.
- **Smart Assignment**:
  - Queries are loaded based on RBAC and status (`Pending`).
  - A query is assignable if it's unassigned, was assigned to another admin over 10 minutes ago, or is already assigned to the current admin.
- **Reply Flow**:
  - Clicking "View" assigns the query to the current admin if available.
  - Only the assigned admin can reply.
  - The reply is stored, and an email notification is sent to the user.

### 🔑 Forgot Password
- Admins can reset their password by entering their email to receive a secure token.

---

## ⚙️ Getting Started

### 1. Clone the repo
```bash
git clone https://github.com/your-username/shaadisharthi-admin.git
cd shaadisharthi-admin
```

### 2. Install dependencies
```bash
npm install
```

### 3. Create `.env` file
Create a `.env` file at the root of the project and add the backend API URL.
```bash
touch .env
```
```env
REACT_APP_API_URL=http://localhost:8080/ShaadiSharthi
```

### 4. Run development server
```bash
npm start
```

---

## ⚠️ Notes
- Frontend admin management features are for UI demonstration; the backend enforces all security rules.
- JWT is stored in local storage for this implementation. Future enhancements will improve token handling.

---

## 🚀 Future Enhancements
- Full audit logs of all admin actions.
- Real-time analytics and dashboard updates.
- Enhanced JWT security (e.g., refresh tokens) and mandatory HTTPS.
- More granular admin role permissions.

## 👨‍💻 Contact

-   **Author**: JAY PATEL — Full Stack Developer (Java + Modern JS Frameworks)
-   **Email**: jayptl565188@example.com
-   **GitHub**: github.com/JayPatel1785651

---

## 📜 License

-   This repository is provided for portfolio and educational purposes.

---
Built with ❤️ for the wedding industry
