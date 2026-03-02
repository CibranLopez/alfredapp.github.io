# 🍽️ Alfred — Restaurant Management System

**Alfred** is a mobile app that helps restaurant and hospitality teams manage everything from inventory and recipes to staff, bookings, and sales—all in one place.

Whether you're running a small café, a busy kitchen, or managing multiple restaurant locations, Alfred keeps your operations organized, efficient, and data-driven.

---

## ✨ What You Can Do With Alfred

### 📦 **Inventory Management**
- Track stock levels in real-time
- Get alerts when items run low  
- View costs and allergen information for every ingredient
- Monitor expiry dates

### 🍳 **Recipe & Dish Management**
- Create recipes (escandallos) with detailed ingredients and portions
- Automatically calculate food costs
- Track allergens and nutritional information
- Manage menu items and pricing

### 📋 **Purchase Orders**
- Create orders from suppliers
- Track order status from creation to delivery
- Match invoices with received goods
- Maintain supplier catalogs

### 👥 **Staff Management**
- Create schedules and shift assignments
- Assign daily tasks to team members
- Track performance metrics
- Monitor hours worked and bonuses

### 📅 **Bookings & Reservations**
- View your restaurant floor plan
- Manage table assignments and capacity
- Accept and track guest bookings
- Assign tables for reservations

### 💰 **Sales & Analytics**
- View real-time revenue reports
- Track profit margins and costs
- Analyze sales by dish or category
- Monitor tips and transactions

### 🏢 **Multi-Location Support**
- Manage multiple restaurant locations from one account
- Different roles (manager, worker, supplier) with different permissions
- Secure login and data separation per location

---

## 🔒 Security & Privacy

✅ **Your data is private.** We don't sell or share your restaurant data.  
✅ **Encrypted storage.** Login tokens are encrypted on your device.  
✅ **Secure authentication.** Your password is hashed and never stored in plain text.  
✅ **HTTPS only.** All communication with our servers is encrypted.

See our **[Privacy Policy](https://raw.githubusercontent.com/CibranLopez/alfredapp/main/docs/privacy_policy.html)** and **[Terms of Service](https://raw.githubusercontent.com/CibranLopez/alfredapp/main/docs/terms_of_service.html)**.

---

## 📲 Download Alfred

**iOS:** Available on the App Store  
**Android:** Available on Google Play Store

---

## 🚀 Getting Started

1. **Download the app** from your device's app store
2. **Sign in** with credentials provided by your restaurant manager
3. **Choose your location** if managing multiple restaurants
4. **Start using** the features matching your role:
   - **Managers:** Full access to all features
   - **Workers:** Inventory, bookings, orders
   - **Suppliers:** View your order history and invoices

---

## 💡 Tips & Tricks

- **Set low-stock alerts:** Get notified before you run out of key ingredients
- **Review analytics daily:** Understand trends in what sells
- **Use floor plan:** Better manage table assignments and reservations
- **Track recipes:** Know the exact cost of every dish you serve
- **Monitor staff hours:** Ensure fair scheduling and payroll accuracy

---

## ❓ Help & Support

### I forgot my password
Contact your restaurant manager to reset your account.

### Something isn't working
Check your internet connection and try again. If the problem persists, contact your administrator.

### Is my data safe?
Yes. Your data is encrypted and stored securely. See our Privacy Policy for details.

### Can I use Alfred offline?
Alfred works best with an internet connection. Some data is cached, but changes require a network connection to save.

---

## 📞 Contact & Information

For support or questions about Alfred:
- **Email:** hello@alfredapp.com
- **Website:** [alfredapp.com](https://alfredapp.com)

---

## 📄 Legal

- [Privacy Policy](https://raw.githubusercontent.com/CibranLopez/alfredapp/main/docs/privacy_policy.html)
- [Terms of Service](https://raw.githubusercontent.com/CibranLopez/alfredapp/main/docs/terms_of_service.html)

---

**Made with ❤️ for restaurant teams everywhere.**

### App Store Connect (iOS)

- [ ] Register App ID `com.alfredapp.alfred` in Apple Developer portal
- [ ] Set Privacy Policy URL: My Apps → App Information → Privacy Policy URL
- [ ] Confirm `DEVELOPMENT_TEAM` in `ios/Runner.xcodeproj/project.pbxproj` matches your team

### Google Play (Android)

- [ ] Create app with package name `com.alfredapp.alfred`
- [ ] Set Privacy Policy URL: Policy → App Content → Privacy Policy
- [ ] Upload signed release APK/AAB (keystore in `key.properties` — do not commit)

### Backend (Render)

After deploying with `render.yaml`, set these in the Render dashboard
(alfred-backend → Environment):

```
JWT_SECRET_KEY         # python3 -c "import secrets; print(secrets.token_hex(32))"
CORS_ALLOWED_ORIGINS   # https://app.alfredapp.com,https://admin.alfredapp.com
```

`FLASK_ENV=production` and `JWT_ACCESS_TOKEN_EXPIRES_MINUTES=15` are already
set in `render.yaml`.

---

## Security notes

- JWT tokens expire after **15 minutes** in production (env var `JWT_ACCESS_TOKEN_EXPIRES_MINUTES`).
- Tokens are stored in iOS Keychain / Android Keystore via `flutter_secure_storage`.
- The backend rejects requests with a missing or placeholder `JWT_SECRET_KEY` at startup — the dyno will fail to start with a clear log message rather than serving with a weak key.
- iOS ATS: `NSAllowsArbitraryLoads` has been removed. Only `localhost` and `127.0.0.1` have an HTTP exception (dev backend). All other hosts require HTTPS.
- Android: `android:usesCleartextTraffic="false"` — no plain HTTP in production builds.

---

## Dependencies

| Package | Version | Purpose |
|---|---|---|
| `http` | ^1.2.0 | HTTP client |
| `flutter_secure_storage` | ^9.2.2 | JWT token storage |
| `url_launcher` | ^6.3.0 | Open Privacy Policy / Terms in browser |
| `google_fonts` | ^6.1.0 | Typography |
| `table_calendar` | ^3.0.0 | Booking calendar UI |
| `file_picker` | ^8.0.6 | Invoice document upload |
| `qr_flutter` | ^4.1.0 | QR payment display |
| `pycryptodome` | 3.21.0 | Redsys 3DES payment signing (backend) |
| `Flask-JWT-Extended` | 4.7.1 | JWT auth (backend) |

---

## Licence

Proprietary. All rights reserved. <!-- TODO(legal): update if open-sourcing -->
