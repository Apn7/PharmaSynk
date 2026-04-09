# PharmaSynk

PharmaSynk is an Android pharmacy/e-commerce application that supports customer shopping workflows and an admin product management panel, backed by Firebase services.

## Why this project stands out (CV-ready summary)
- Built a multi-screen Android application in **Java** with **Navigation Drawer + Fragments + RecyclerViews**.
- Implemented end-to-end customer flow: **authentication → product discovery → cart → address → payment → order history**.
- Integrated **Firebase Auth**, **Cloud Firestore**, **Realtime Database**, and **Firebase Storage**.
- Added an **admin control panel** for product **add / modify / delete** operations.
- Used modern Android tooling: **Gradle Kotlin DSL**, **ViewBinding**, and common UI/image/network libraries.

## Tech stack
- **Language:** Java
- **Platform:** Android (minSdk 28, targetSdk 34, compileSdk 34)
- **Build:** Gradle (Kotlin DSL), Android Gradle Plugin 8.1.2
- **Backend/Cloud:** Firebase Auth, Firestore, Realtime Database, Storage
- **Libraries:** Volley, Glide, Lottie, Material Components, AndroidX Navigation

## Features
### Customer features
- Splash + welcome entry flow
- Email/password user registration and login
- Home feed with suggested products and categories
- Product search by name/type (Firestore query)
- Product detail pages with quantity selection
- Add-to-cart and cart total calculation
- Address management for checkout
- Payment summary and order placement workflow
- Order history view
- Medicine info screen (external JSON API + detail view)

### Admin features
- Separate admin login entry
- Admin panel for:
  - Add product (including image upload to Firebase Storage)
  - Modify existing product
  - Delete product

## Codebase index

Repository root:
- `./README.md` — project documentation
- `./Projecto2/` — Android application source

Android project core:
- `./Projecto2/settings.gradle.kts` — module/repository settings
- `./Projecto2/build.gradle.kts` — top-level build config
- `./Projecto2/app/build.gradle.kts` — app dependencies and Android config
- `./Projecto2/app/src/main/AndroidManifest.xml` — app manifest and activity registration

Main Java packages:
- `com.example.projecto`
  - `MainActivity.java` — navigation drawer host activity
  - `MycartsFragment.java` — cart screen + totals
  - `MyordersFragment.java` — order history screen
- `com.example.projecto.ui.home`
  - `HomeFragment.java` — suggested/category feed + search
- `com.example.projecto.ui.category`
  - `CategoryFragment.java` — medicine info list from remote JSON
- `com.example.projecto.ui.profile`
  - `ProfileFragment.java` — profile placeholder screen
- `com.example.projecto.activities`
  - Authentication/entry: `Splashscreen`, `Welcome`, `LoginActivity`, `RegisterActivity`
  - Product browsing/details: `ViewAllActivity`, `DetailActivity`, `DetailActivity2`
  - Checkout: `AddressActivity`, `AddAddressActivity`, `PaymentActivity`, `OrderPlaced`
  - Admin: `AdminLoginActivity`, `AdminPanel`, `AddProducts`, `ModifyProducts`, `DeleteProducts`
  - Info utility: `UseDetails`
- `com.example.projecto.adapters`
  - Recycler/List adapters for categories, products, cart, orders, and addresses
- `com.example.projecto.models`
  - Data models such as `ViewAllModel`, `SuggestedModel`, `MyCartModel`, `AddressModel`, etc.

Resources:
- `./Projecto2/app/src/main/res/layout/` — screen/layout XML files
- `./Projecto2/app/src/main/res/navigation/mobile_navigation.xml` — nav graph
- `./Projecto2/app/src/main/res/menu/` — top app bar + drawer menus
- `./Projecto2/app/src/main/res/drawable/` and `mipmap*/` — image/vector assets

## Data & backend notes
- Firestore collections used in app logic include:
  - `Allproducts`
  - `Suggested`
  - `Category`
  - `CurrentUser/{uid}/AddToCart`
  - `CurrentUser/{uid}/MyOrders`
  - `CurrentUser/{uid}/Address`
- Realtime Database is used for user profile registration data (`Users/{uid}`).
- Firebase configuration file is present at:
  - `./Projecto2/app/google-services.json`

## Setup & run
1. Open `./Projecto2` in Android Studio.
2. Ensure Android SDK platform 34 is installed.
3. Ensure a compatible JDK is configured (AGP 8.x typically uses Java 17).
4. Sync Gradle.
5. Run app on emulator or device.

CLI commands (from `./Projecto2`):
```bash
./gradlew test
./gradlew lint
./gradlew assembleDebug
```

## Validation status in this environment
- Attempted: `./gradlew test lint assembleDebug --no-daemon`
- Result: failed in sandbox due to Gradle plugin resolution issue (`com.android.application` plugin could not be resolved from configured repositories).
- Note: this is typically environment/network/repository-access related; run via Android Studio or a fully network-enabled Gradle environment.
