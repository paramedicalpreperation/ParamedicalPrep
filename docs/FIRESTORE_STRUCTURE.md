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
