# Product Catalog Application

A Flutter Product Catalog application built as part of the Flutter Developer Technical Assessment.

The app fetches product data from the Fake Store API and allows users to view product listings, search products, see product details, and manage favorite products locally.

## Features

* Fetch products from API
* Display product image, title, price, and rating
* Product details screen
* Search products by title
* Add and remove favorite products
* Favorite products remain saved after app restart
* Loading state handling
* Error state with retry option
* Empty state handling
* Pull-to-refresh functionality
* Responsive UI
* Dark mode support
* Cached network images

## API Used

```txt
https://fakestoreapi.com/products
```

## Project Setup Instructions

### Prerequisites

Make sure Flutter is installed on your machine.

Check Flutter installation:

```bash
flutter doctor
```

### Clone the Repository

```bash
git clone YOUR_GITHUB_REPOSITORY_LINK
cd product_catalog_app
```

### Install Dependencies

```bash
flutter pub get
```

### Run the Application

For Android emulator or physical device:

```bash
flutter run
```

For a specific Android device:

```bash
flutter devices
flutter run -d DEVICE_ID
```

### Build APK

Debug APK:

```bash
flutter build apk --debug
```

Release APK:

```bash
flutter build apk --release
```

APK output location:

```txt
build/app/outputs/flutter-apk/
```

## Architecture Explanation

This project follows a simple MVVM-style architecture to keep the code clean, maintainable, and easy to understand.

### Folder Structure

```txt
lib/
  models/
    product_model.dart

  services/
    product_service.dart

  viewmodels/
    product_view_model.dart

  views/
    product_list_screen.dart
    product_details_screen.dart

  widgets/
    product_card.dart

  main.dart
```

### Architecture Layers

#### Model

The model represents the product data structure.

Example:

```txt
Product model contains:
- id
- title
- price
- description
- category
- image
- rating
- rating count
```

#### Service

The service layer is responsible for API communication.

`ProductService` fetches product data from the Fake Store API and converts the JSON response into Product objects.

#### ViewModel

The ViewModel contains the main business logic of the application.

It handles:

* Fetching products
* Loading state
* Error state
* Search logic
* Favorite product logic
* Saving and loading favorite products from local storage

#### View

The views are responsible for displaying UI to the user.

Main screens:

* Product Listing Screen
* Product Details Screen

#### Widgets

Reusable UI components are placed inside the widgets folder.

Example:

* ProductCard

## State Management Explanation

This project uses Provider for state management.

Provider was selected because it is simple, beginner-friendly, and suitable for small to medium Flutter applications.

The main state is managed inside `ProductViewModel`, which extends `ChangeNotifier`.

When data changes, `notifyListeners()` is called to update the UI automatically.

The following states are handled using Provider:

* Product list state
* Loading state
* Error state
* Search result state
* Favorite product state

The app avoids using `setState` as the primary state management solution.

## Favorites Persistence

Favorite products are stored locally using SharedPreferences.

Only favorite product IDs are saved locally. When the app restarts, saved favorite IDs are loaded again, so the user can see previously selected favorite products.

## Third-party Packages Used

### provider

Used for state management.

```yaml
provider
```

### http

Used for calling the Fake Store API.

```yaml
http
```

### shared_preferences

Used for saving favorite product IDs locally.

```yaml
shared_preferences
```

### cached_network_image

Used for loading and caching product images from the internet.

```yaml
cached_network_image
```

## Development Standards Followed

* Flutter Null Safety
* Clean and readable code
* Proper naming conventions
* Separation of concerns
* Reusable widgets
* Responsive UI
* Error handling
* Local data persistence

## How to Test the App

After running the app, test the following:

1. Product list loads successfully.
2. Product image, title, price, and rating are displayed.
3. Tapping a product opens the details screen.
4. Search works dynamically while typing.
5. Favorite button adds and removes favorite products.
6. Favorite status remains after restarting the app.
7. Pull-to-refresh reloads product data.
8. Error and empty states are handled properly.


