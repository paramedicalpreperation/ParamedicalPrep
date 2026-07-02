# Firestore Structure

This document defines the complete Firebase Firestore architecture used by the Paramed Prep application.

The structure is designed for scalability, performance, offline support and future expansion.

## Design Goals

The Firestore architecture must:

- Support millions of questions.

- Support unlimited courses.

- Support offline-first learning.

- Minimize Firebase read operations.

- Be fast on slow internet.

- Be easy to maintain.

- Be scalable without redesign.

- Support future features without database migration.

## Collections

The Firestore database is divided into top-level collections.

Version 1 uses the following collections:

- courses

- questions

- users

- mock_tests

- app_config

Future collections may include:

- leaderboard

- notifications

- subscriptions

- analytics

- reports

- payments

Rules:

- Every collection has a single responsibility.

- Collections should remain independent whenever possible.

- Avoid deeply nested collections.

- Keep document size small.

- Design for scalability from the beginning.

## Collections

The Firestore database is divided into top-level collections.

Version 1 uses the following collections:

- courses

- questions

- users

- mock_tests

- app_config

Future collections may include:

- leaderboard

- notifications

- subscriptions

- analytics

- reports

- payments

Rules:

- Every collection has a single responsibility.

- Collections should remain independent whenever possible.

- Avoid deeply nested collections.

- Keep document size small.

- Design for scalability from the beginning.

## Database Tree

Version 1 Firestore Structure:

courses/
    {courseId}

questions/
    {questionId}

users/
    {userId}

mock_tests/
    {mockTestId}

app_config/
    settings

Future Collections:

leaderboard/
notifications/
subscriptions/
analytics/
reports/
payments/

## Courses Collection

The courses collection stores all available courses.

Each course is stored as one document.

Document ID Examples:

- MLT

- RD

- CCT

Future Examples:

- OT

- ECG

- DIALYSIS

- PHYSIOTHERAPY

Each course contains:

- Course ID

- Course Name

- Short Name

- Description

- Icon

- Banner Image

- Color Theme

- Display Order

- Total Subjects

- Total Topics

- Total Questions

- Active Status

Rules:

- Course ID never changes.

- Display Order controls the home screen order.

- Active courses are visible to users.

- Disabled courses remain in the database but are hidden from users.

- New courses can be added without modifying the application structure.

## Database Design Principle

All major entities are stored as top-level collections.

Examples:

- courses

- subjects

- topics

- questions

- users

- mock_tests

Relationships are maintained using unique IDs instead of deeply nested collections.

This architecture improves scalability, performance, maintainability and querying efficiency.

## Subjects Collection

The subjects collection stores all subjects available under different courses.

Each subject belongs to one course.

Each subject is stored as one document.

Examples:

- Anatomy

- Physiology

- Pathology

- Microbiology

- Pharmacology

- Radiographic Physics

Each subject contains:

- Subject ID

- Subject Name

- Subject Code

- Course ID

- Icon

- Display Order

- Total Topics

- Total Questions

- Active Status

Rules:

- Subject ID never changes.

- Every subject references its parent Course ID.

- Display Order controls the sequence within a course.

- Active subjects are visible to users.

- Disabled subjects remain in the database but are hidden from users.

- New subjects can be added without modifying the application structure.

## Topics Collection

The topics collection stores all topics under different subjects.

Each topic belongs to one subject.

Each topic is stored as one document.

Examples:

- Upper Limb

- Lower Limb

- Thorax

- Abdomen

- Skull

- Contrast Media

- Radiation Protection

- Bacteria

- Blood Banking

Each topic contains:

- Topic ID

- Topic Name

- Topic Code

- Subject ID

- Course ID

- Display Order

- Total Questions

- Active Status

Rules:

- Topic ID never changes.

- Every topic references its parent Subject ID and Course ID.

- Display Order controls the sequence within a subject.

- Active topics are visible to users.

- Disabled topics remain in the database but are hidden from users.

- New topics can be added without modifying the application structure.

## Questions Collection

The questions collection stores all questions used in the Paramed Prep application.

Each question is stored as one document.

Every question references its related Course, Subject and Topic using unique IDs.

Each question contains:

- Question ID

- Course ID

- Subject ID

- Topic ID

- Subtopic (Optional)

- Question Type

- Difficulty Level

- Language

- Question Text

- Question Image (Optional)

- Options

- Correct Option ID

- Explanation

- Explanation Image (Optional)

- Explanation Video (Optional)

- Clinical Tip (Premium)

- Did You Know (Premium)

- References

- Previous Year Question Details (Optional)

- Tags

- Status

- Schema Version

- Created At

- Updated At

Rules:

- Question ID never changes.

- Questions are never permanently deleted.

- Archived questions remain available for future use.

- Every question references Course ID, Subject ID and Topic ID.

- Every question supports future multilingual content.

- Every question is designed for offline synchronization.

- The document structure must remain lightweight for fast performance.

## Users Collection

The users collection stores user account information and learning progress.

Each user is stored as one document.

Each user contains:

- User ID

- Full Name

- Email Address

- Mobile Number (Optional)

- Profile Photo (Optional)

- Preferred Language

- Selected Course

- Subscription Type

- Subscription Expiry (Optional)

- Total XP

- Current Streak

- Longest Streak

- Total Questions Solved

- Total Mock Tests Attempted

- Account Status

- Created At

- Updated At

Rules:

- User ID never changes.

- Personal information is stored securely.

- Learning statistics are updated automatically.

- User data is synchronized across devices after login.

- Inactive accounts remain in the database unless permanently removed by the user.

## Bookmarks Collection

The bookmarks collection stores questions bookmarked by users for future revision.

Each bookmark is stored as one document.

Each bookmark contains:

- Bookmark ID

- User ID

- Question ID

- Created At

Rules:

- One user can bookmark multiple questions.

- One question can be bookmarked by multiple users.

- Duplicate bookmarks are not allowed.

- Removing a bookmark does not affect the original question.

- Bookmarks are synchronized across devices after login.

## Progress Collection

The progress collection stores the learning progress of every user.

Each progress record is stored as one document.

Each progress document contains:

- Progress ID

- User ID

- Question ID

- Selected Option ID

- Correct Option ID

- Attempt Number

- Is Correct

- Time Taken

- Answered At

- Sync Status

Rules:

- One document is created for each answered question.

- Progress is synchronized automatically after internet is available.

- Progress supports offline learning.

- Progress history helps generate analytics, revision plans and AI recommendations.

- Progress records are never overwritten. New attempts create updated progress entries while preserving learning history where required.

## Mock Tests Collection

The mock_tests collection stores all mock tests available in the application.

Each mock test is stored as one document.

Each mock test contains:

- Mock Test ID

- Mock Test Name

- Course ID

- Subject ID (Optional)

- Topic ID (Optional)

- Total Questions

- Total Marks

- Duration

- Positive Marks

- Negative Marks

- Passing Marks (Optional)

- Difficulty Level

- Language

- Question List

- Active Status

- Created At

- Updated At

Rules:

- Every mock test has a unique Mock Test ID.

- A mock test may include questions from one or multiple subjects.

- Questions are referenced using Question IDs.

- Mock tests can follow different official examination patterns.

- Mock tests remain editable without affecting previous user attempts.

## Mock Attempts Collection

The mock_attempts collection stores every mock test attempt made by users.

Each attempt is stored as one document.

Each mock attempt contains:

- Attempt ID

- User ID

- Mock Test ID

- Attempt Number

- Started At

- Submitted At

- Time Taken

- Total Questions

- Correct Answers

- Wrong Answers

- Unanswered Questions

- Final Score

- Percentage

- Accuracy

- Rank (Future)

- Result Status

- Attempt Status

Rules:

- Every attempt has a unique Attempt ID.

- Previous attempts are never overwritten.

- Every attempt remains available for future review.

- Analytics are generated from attempt history.

- Attempt history supports AI-based recommendations and revision planning.

- Mock attempts remain linked to the original Mock Test even if the mock is updated later.

## App Config Collection

The app_config collection stores global application settings.

Each configuration is stored as one document.

Examples:

- General Settings

- App Version

- Maintenance Mode

- Home Banner

- Featured Mock Tests

- Daily Challenge

- Update Message

- Minimum Supported Version

- Premium Plans

Rules:

- Configuration changes should not require an app update.

- The application automatically fetches the latest configuration.

- Configuration data should remain lightweight.

- Only administrators can modify configuration values.

- Changes take effect immediately after synchronization.

## Security Rules

The Firestore database must follow strict security rules.

Rules:

- Users can access only their own personal data.

- Users cannot modify question content.

- Only administrators can create, update or archive questions.

- Only administrators can manage courses, subjects, topics and mock tests.

- Every write operation must be authenticated.

- Sensitive data must never be publicly accessible.

- Firestore Security Rules must be enabled before production release.

## Synchronization Strategy

The application follows an Offline-First synchronization model.

Rules:

- User actions are saved locally first.

- Synchronization starts automatically when internet is available.

- Synchronization runs silently in the background.

- Failed synchronization attempts are automatically retried.

- Duplicate records are prevented using unique document IDs.

- Synchronization must never interrupt the user experience.

## Firestore Indexing Strategy

Indexes are created for frequently queried fields.

Examples:

- Course ID

- Subject ID

- Topic ID

- Difficulty Level

- Language

- Status

- Previous Year Question

Rules:

- Only required indexes should be created.

- Avoid unnecessary composite indexes.

- Optimize queries to reduce Firebase read costs.
