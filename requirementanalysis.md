<div align="center">

# BuildShare: Requirements Specification

</div>

## Table of Contents

- [1. Project Statement](#1-project-statement)
- [2. Stakeholders and User Groups](#2-stakeholders-and-user-groups)
- [3. Motivation for Use](#3-motivation-for-use)
- [4. Example Use Scenario](#4-example-use-scenario)
- [5. Requirements Analysis](#5-requirements-analysis)
  - [5.1 Functional Requirements](#51-functional-requirements)
  - [5.2 Non-functional Requirements](#52-non-functional-requirements)
- [6. Technical and Software Constraints](#6-technical-and-software-constraints)
- [7. Evaluation Criteria](#7-evaluation-criteria)

---

## 1. Project Statement

BuildShare is a mobile-first gaming platform developed using React Native (via Expo) where users can share detailed builds for specific games and characters, participate in game-specific forums, and interact with others through likes, comments, follows, and favorites. The backend is powered by Firebase Firestore and authentication is handled through Clerk with Google login. The platform aims to provide a centralized hub where players can find and contribute to strategic game content. BuildShare encourages community interaction through a modern, scalable architecture supporting real-time updates and user-driven engagement features.

---

## 2. Stakeholders and User Groups

1. **End Users (Gamers)**

   - Players of games like Dota 2, LoL, Elden Ring who want to share and discover builds.
   - Strategy-focused gamers interested in community insights, gameplay efficiency, and discussion.

2. **Developer and Moderator**
   - Bekir Görkem Özhan (solo developer during MVP) responsible for development and moderation.
   - Future moderators or contributors who may manage user-generated content and assist with feature suggestions.

---

## 3. Motivation for Use

- **Centralized Build Library**  
  Players need a focused platform to find and share builds without external distractions.

- **Community Interaction and Strategy Sharing**  
  The system supports in-depth discussions and feedback loops to refine builds.

- **Convenience and Time Saving**  
  Filtering tools, AI summaries, and a visual-friendly UI allow gamers to quickly access relevant content before or during gameplay.

---

## 4. Example Use Scenario

### 4.1 User Story

> Görkem wants to try a new strategy for Troll Warlord in Dota 2. He opens BuildShare, logs in using Google, and selects Dota 2 from the games list. He browses builds and finds a popular “Berserk Attack Build”. He favorites the build, follows the user, and later decides to share his own version through the Add Build modal. As others interact with his build, he earns badges based on upvotes and participation. Görkem later revisits the build comments to refine it based on feedback.

---

## 5. Requirements Analysis

### 5.1 Functional Requirements

1. **Authentication and Profile**

   - Users can sign in using Clerk (Google login).
   - Users see only their nickname and can log out.
   - Logging out redirects to the sign-in page.

2. **Build Sharing System**

   - Builds can be created via a modal in `builds.tsx`.
   - New builds appear immediately after submission.
   - Builds are linked to selected game and character only.
   - Only the build creator can delete it.
   - Users can upvote a build once, and also comment on builds.
   - Comments display in real-time and can be deleted by the owner.

3. **Forum System**

   - Users can write public game-specific posts.
   - Each forum post has its own detail page (`forum/[id].tsx`).
   - Users can comment on forum posts, and these are shown live.
   - Users can delete their own forum comments.

4. **Engagement Features**

   - Users can favorite builds and follow others.
   - A badge system rewards activity and positive engagement.
   - YouTube video guides can be attached to builds for visual aid.

5. **AI Integration (Build Summary)**
   - An AI system analyzes long build descriptions.
   - The system summarizes content to highlight key points.
   - Summarization improves readability and saves player time.

---

### 5.2 Non-functional Requirements

1. **Performance**

   - Build and comment actions must complete in under 3 seconds.
   - No freezing or lag during Firestore operations.

2. **Usability**

   - Mobile-first UI with responsive layout and accessible fonts.
   - Easy-to-use interface for fast navigation and contribution.

3. **Security and Privacy**

   - Only nicknames are displayed publicly (no emails).
   - Data must be encrypted during transmission.
   - Only logged-in users can post, comment, or vote.

4. **Scalability**

   - Firestore should support increasing numbers of users, games, and builds.
   - System should maintain speed and responsiveness as usage scales.

5. **Reliability and Error Handling**

   - Clear error messages must be shown for failed actions.
   - System should attempt retries in case of intermittent issues.

6. **Maintainability**
   - Codebase must use reusable components and modular design.
   - Components like BuildCard, CommentBox, and ForumPost must be reusable and documented.

---

## 6. Technical and Software Constraints

- **Operating System**: Android, iOS
- **Programming Languages**: JavaScript (React Native), optional Python for AI summarization
- **Frameworks & Libraries**:
  - **Frontend**: Expo + React Native
  - **Backend**: Firebase Firestore (NoSQL), Clerk Auth
  - **AI Summary (optional)**: Python, OpenAI or custom summarizer
- **Navigation**: React Navigation with `_layout.tsx` structure
- **IDE**: Visual Studio Code
- **Note**: Image/avatar uploads are currently disabled

---

## 7. Evaluation Criteria

1. **Functionality**

   - Build creation, voting, and forum systems should work seamlessly.
   - All user interactions must be real-time and responsive.

2. **Performance**

   - Average response times must stay under 3 seconds.
   - Firestore scalability must be ensured.

3. **User Experience**

   - The UI should be clear and intuitive.
   - User should be able to quickly discover, post, and interact with content.

4. **Stability & Security**
   - No crashes or unauthorized access should occur.
   - Public data display must comply with privacy policies.

---
