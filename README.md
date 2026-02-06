# 🚀 iOS To-Do App with Firebase (MVC)

A real-time, efficient task management application built with **Swift** and **UIKit**. This project utilizes the **MVC (Model-View-Controller)** design pattern and **Firebase Realtime Database** for instant data synchronization.

<p align="center">
  <img src="ToDoApp/img/IMG_5834.PNG" alt="Home Screen" width="200"/>
  <img src="ToDoApp/img/IMG_5836.PNG" alt="Search" width="200"/>
  <img src="ToDoApp/img/IMG_5835.PNG" alt="Add Task" width="200"/>
</p>

## 🌟 Key Features

* **Real-Time Sync:** Tasks are instantly synchronized across devices using Firebase Realtime Database.
* **MVC Architecture:** Standard iOS architecture where the View Controller manages the data flow and UI updates.
* **Smart Search (Debouncing):** Optimized search performance using timers to reduce database queries.
* **Safe Swipe-to-Delete:** Crash-free deletion logic with index safety checks.
* **Custom UI:** Specialized table view cells with dynamic styling (strike-through text for completed tasks).
* **Keyboard Handling:** Improved UX with easy keyboard dismissal gestures.

## 🛠 Tech Stack

| Category | Technology |
| --- | --- |
| **Language** | Swift 5 |
| **Framework** | UIKit |
| **Architecture** | MVC (Model-View-Controller) |
| **Backend** | Firebase Realtime Database |
| **Dependency Manager** | Swift Package Manager (SPM) |

## 🏗 How It Works

This app follows the classic **MVC** pattern:
* **Model:** `Task` struct. It handles the JSON mapping from Firebase snapshots.
* **View:** `TaskCell` and Storyboard layouts.
* **Controller:** `TaskListViewController`. It acts as the brain, listening to Firebase updates (`observe(.value)`), managing the `TableView`, and handling user interactions.

### Code Highlight: Debounced Search
To prevent UI lag during searching, a throttling mechanism is used:
```swift
searchTimer?.invalidate()
searchTimer = Timer.scheduledTimer(withTimeInterval: 0.5, repeats: false) { ... }
