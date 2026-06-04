# Firebase Setup Guide for E-Learning Portal

## Step 1: Create Firebase Project

1. Go to https://console.firebase.google.com/
2. Click "Add Project"
3. Name it: `kis-bpa-elearning`
4. Disable Google Analytics (not needed)
5. Click "Create Project"

## Step 2: Enable Authentication

1. In Firebase Console → Click "Authentication" (left menu)
2. Click "Get Started"
3. Enable "Email/Password" sign-in method
4. Click Save

## Step 3: Create Firestore Database

1. Click "Firestore Database" (left menu)
2. Click "Create Database"
3. Select "Start in test mode" (we'll add security later)
4. Choose nearest location (asia-south1 for India)
5. Click "Enable"

## Step 4: Get Firebase Config

1. Click the gear icon → "Project Settings"
2. Scroll down to "Your apps" → Click web icon (</>)
3. Register app name: `kis-elearning`
4. Copy the firebaseConfig object
5. Paste it in `elearning.html` where indicated (replace the placeholder config)

## Step 5: Database Structure (Auto-created by the app)

```
users/
  {userId}/
    name: "User Name"
    phone: "9876543210"
    email: "user@email.com"
    address: "House No / Address"
    createdAt: timestamp

enrollments/
  {userId}/
    courses/
      {courseId}/
        status: "in-progress" | "completed"
        progress: 65
        enrolledAt: timestamp
        completedAt: timestamp (if completed)

courses/
  quran/
    title: "ഖുർആൻ പഠനം"
    description: "തജ്‌വീദ്, ഹിഫ്‌ള്, തഫ്‌സീർ"
    duration: "12 weeks"
    totalClasses: 36
    icon: "book-quran"
  fiqh/
    ...
```

## Step 6: Deploy

After setup, your E-Learning portal will have:
- Real user registration & login
- Course enrollment saved in database
- Progress tracking
- Persistent data (won't lose on page refresh)
- Admin can see all users & their progress in Firebase Console
