# Question Model

This document defines the structure and standards for every question used in the Paramed Prep application.

## Question ID

Every question must have a unique Question ID.

Format:

COURSE-SUBJECT-TOPIC-000001

Example:

RD-ANATOMY-HEADNECK-000001

MLT-MICROBIOLOGY-BACTERIA-000245

CCT-PHARMACOLOGY-ANTIBIOTICS-000031

## Course

Every question belongs to one course.

Examples:

- MLT (Medical Laboratory Technology)

- RD (Radio Diagnosis)

- CCT (Critical Care Technology)

 Only these three courses will be used in Version 1. The architecture supports adding unlimited future courses without changing the app structure.

 ## Subject

Every question belongs to one subject within a course.

Examples:

- Anatomy

- Physiology

- Pathology

- Microbiology

- Pharmacology

- Radiographic Physics

A subject can contain multiple topics.

Each subject will have a unique Subject Code.

Examples:

- ANAT = Anatomy

- PHYS = Physiology

- PATH = Pathology

- MICRO = Microbiology

- PHARM = Pharmacology

Subject Codes help in filtering, analytics, searching and maintaining a scalable database.

## Topic

Every subject contains one or more topics.

Examples:

- Upper Limb

- Lower Limb

- Thorax

- Abdomen

- Skull

- Contrast Media

- Radiation Protection

- Bacteria

- Virus

- Blood Banking

Every topic belongs to only one subject.

Topics are used for:

- Practice by Topic

- Mock Test Generation

- Progress Tracking

- Performance Analytics

Each topic will have a unique Topic Code.

Examples:

- UL = Upper Limb

- LL = Lower Limb

- THX = Thorax

- ABD = Abdomen

- SKL = Skull

- CM = Contrast Media

- RP = Radiation Protection

Topic Codes help maintain a clean, searchable and scalable database.

## Subtopic (Optional)

Subtopic is optional.

It should only be used where a topic requires further classification.

Examples:

Anatomy
→ Upper Limb
→ Shoulder

Anatomy
→ Upper Limb
→ Forearm

Microbiology
→ Bacteria
→ No Subtopic

Pharmacology
→ Antibiotics
→ No Subtopic

If a subtopic is not required, the field should remain empty.

This approach keeps the database simple while allowing detailed categorization where necessary.

## Question Type

Every question must have a Question Type.

Supported Question Types (Version 1):

- Single Correct MCQ

Future Supported Types:

- Multiple Correct MCQ

- True / False

- Assertion & Reason

- Match the Following

- Image Based Question

- Case Based Question

- Clinical Scenario

- Numerical Value

Version 1 of Paramed Prep will use only Single Correct MCQ.

The database structure is designed to support additional question types in future without requiring major changes.

## Difficulty Level

Every question must have a Difficulty Level.

Difficulty Levels:

- Easy

- Medium

- Hard

Difficulty Level is stored in the database for analytics, smart practice and adaptive learning.

It is not displayed to users in Version 1.

The system may automatically recommend a difficulty level in future versions based on user performance.

## Language

Every question must have a primary language.

Supported Languages (Version 1):

- English

Future Supported Languages:

- Bengali

- Hindi

- Other Indian Languages

Questions will be stored in English by default.

The application architecture supports multilingual content without changing the database structure.

Machine translation may be available in future versions.

Medical terminology should remain in its original form wherever appropriate to maintain accuracy.

## Question

Every question must contain a clear, accurate and exam-oriented question statement.

Questions should:

- Be grammatically correct.

- Be free from spelling mistakes.

- Follow official exam standards.

- Be easy to read and understand.

- Support English, Bengali and other future languages.

Questions may include:

- Plain Text

- Multi-line Text

- Numbering

- Bullet Points

- Roman Numerals

- Medical Symbols

- Scientific Symbols

- Tables (Future)

Long questions should be properly formatted with appropriate spacing to improve readability on mobile and tablet devices.

## Question Image (Optional)

A question may include one or more images when required.

Question Images may include:

- X-ray

- CT Scan

- MRI

- Ultrasound

- ECG

- Histopathology Slides

- Microscopy Images

- Clinical Photographs

- Medical Instruments

- Anatomy Diagrams

- Charts and Graphs

Rules:

- Images are optional.

- Images must be high quality.

- Images must remain clear after zooming.

- Images must load quickly.

- Images must never reduce application performance.

- Images are stored separately from the question data and linked using image references.

Image-based questions are treated as standard MCQs with optional question images.

## Options

Every question must contain four options in Version 1.

Option Format:

- Option A

- Option B

- Option C

- Option D

Each option may contain:

- Plain Text

- Multi-line Text

- Medical Symbols

- Scientific Symbols

- Image (Optional)

- Tables (Future)

Rules:

- Only one correct answer is supported in Version 1.

- Options must be clear and unambiguous.

- Options should follow a consistent format throughout the application.

Future versions will support Multiple Correct Questions without changing the database structure.

## Correct Answer

Every question must have one correct answer in Version 1.

Supported Values:

- A

- B

- C

- D

Rules:

- Exactly one correct answer is required.

- The correct answer is never displayed before the user submits a response.

- After submission, the correct answer is highlighted automatically.

Future versions may support multiple correct answers without changing the database structure.

## Explanation

Every question must include an explanation.

The explanation should:

- Clearly explain why the correct answer is correct.

- Explain why the other options are incorrect whenever necessary.

- Be concise, accurate and easy to understand.

- Follow official medical references and standard textbooks.

- Be grammatically correct.

- Be free from spelling mistakes.

- Support multi-line formatting.

- Support medical and scientific terminology.

Rules:

- Explanation is mandatory.

- A short preview is shown by default.

- Users can expand the explanation using "Read More".

- The application remembers the expanded state until the user moves to the next question.

  ## Explanation Image (Optional)

An explanation may include one or more images to improve understanding.

Explanation Images may include:

- Anatomy Diagrams

- X-ray Images

- CT Scan

- MRI

- Ultrasound

- ECG

- Histopathology Slides

- Microscopy Images

- Clinical Photographs

- Flowcharts

- Tables

Rules:

- Explanation images are optional.

- Images must be clear and high quality.

- Images should support pinch-to-zoom.

- Images should load efficiently.

- Explanation images must remain linked to their respective question.

  ## Explanation Video (Optional)

An explanation may include a video for better understanding.

Explanation Videos may include:

- Concept Explanation

- Practical Demonstration

- Clinical Procedure

- Animation

- 3D Anatomy

Rules:

- Explanation videos are optional.

- Videos are streamed and are not downloaded automatically.

- Videos should open in the built-in player.

- Users can continue reading the explanation while watching the video.

- Videos must not affect application performance.

- Premium-only videos are supported.

  ## Clinical Tip (Premium)

Clinical Tip provides practical knowledge beyond examination preparation.

Clinical Tips may include:

- Clinical Correlation

- Practical Experience

- Hospital Workflow

- Common Mistakes

- Patient Safety

Rules:

- Clinical Tip is optional.

- Available only for Premium users.

- Clinical Tips must be concise, practical and evidence-based.

  ## Did You Know (Premium)

Did You Know provides interesting facts related to the topic.

Examples:

- Historical Facts

- Medical Discoveries

- Recent Guidelines

- Exam Tricks

Rules:

- Did You Know is optional.

- Available only for Premium users.

- Information must be authentic and reference-based.

  ## Reference

Every question should be supported by at least one authentic reference whenever possible.

References may include:

- Standard Medical Textbooks

- Government Guidelines

- National Health Programmes

- Official Protocols

- Peer-Reviewed Journals

Examples:

- Gray's Anatomy (42nd Edition)

- Guyton & Hall Textbook of Medical Physiology

- Robbins & Cotran Pathologic Basis of Disease

- Park's Textbook of Preventive and Social Medicine

- Bontrager's Textbook of Radiographic Positioning and Related Anatomy

- Merrill's Atlas of Radiographic Positioning and Procedures

Rules:

- References should be authentic and up-to-date.

- References should be displayed below the explanation.

- Multiple references are supported.

- References are optional but strongly recommended.

  ## Previous Year Question (PYQ)

A question may be marked as a Previous Year Question.

If enabled, the following information can be stored:

- Exam Name

- Recruitment Board

- Year

- Shift (Optional)

- Question Number (Optional)

Rules:

- PYQ is optional.

- A question may belong to multiple examinations.

- The application displays only a small "Asked in X Exams" badge below the question.

- Tapping the badge shows the complete examination history.

  ## Bookmark

Users can bookmark questions for future revision.

Rules:

- Bookmark is optional.

- A bookmarked question is linked to the user's account.

- Bookmarks are synchronized across devices after login.

- Bookmarked questions remain available until removed by the user.

- Deleting a bookmark does not affect the original question.

  ## Report Question

Users can report a question if they find any issue.

Reasons may include:

- Incorrect Answer

- Incorrect Explanation

- Typographical Error

- Image Issue

- Outdated Information

- Duplicate Question

- Other

Rules:

- Reporting is optional.

- Reports are sent to the administration panel.

- Multiple users can report the same question.

- Reported questions remain available until reviewed by an administrator.

  ## Question Status

Every question must have a status.

Supported Status:

- Draft

- Published

- Archived

Rules:

- Draft questions are visible only to administrators.

- Published questions are available to users.

- Archived questions are hidden from users but remain stored in the database.

  ## Version

Every question maintains a version number.

Rules:

- Version starts from 1.

- The version increases whenever the question content is updated.

- Version history helps maintain quality and track changes.

  ## Last Updated

Every question stores its last updated date and time.

Rules:

- Updated automatically whenever the question is modified.

- Used for synchronization, quality control and future auditing.

  ## Summary

This document defines the complete structure of a question used in the Paramed Prep application.

The model is designed to be scalable, maintainable and future-ready while supporting high-quality medical education and examination preparation.
