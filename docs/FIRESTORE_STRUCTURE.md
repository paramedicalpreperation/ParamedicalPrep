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
