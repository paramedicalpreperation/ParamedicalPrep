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
