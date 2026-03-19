# RFC

## Problem Statement
Currently, all knowledge sharing is kept on Telegram and on the machine running OpenClaw. The main issue is that when I need to search for or revisit a specific concept, news, or data, I have to sift through numerous messages exchanged between OpenClaw and me, which is time-consuming. Often, I end up searching on the browser and looking for the information again instead.

## Goals & Non-Goals

**Goals**
1. Persist information in a centralized location
2. Enable easy search and filtering of information by category
3. Support full CRUD operations on saved information
4. Have all information validated and updated by an LLM for accuracy
5. Maintain separate frontend and backend architectures
6. Run locally

**Non-Goals**
1. Multi-user access—this is a personal learning organization tool
2. Integration with authentication services

## User Story

### Epic
As a user, I want to open this app every morning to view the latest updates from the Python and programming communities (such as news from Y Combinator). I also want to see my daily agenda and take tests on the knowledge I've acquired. Additionally, I want a view to revisit and review learning materials from the past week.

### Decomposed Stories

#### Story 1: View Latest Community Updates
As a user, I want to view the latest updates and news from the Python and programming communities (e.g., Y Combinator), so that I can stay informed about recent developments in my field of interest.

**Acceptance Criteria:**
- Display a feed of latest news articles from configured sources
- Show article title, summary, and source
- Allow filtering by community/source

#### Story 2: Access Daily Agenda
As a user, I want to see my daily agenda when I open the app, so that I can plan my day and manage my schedule.

**Acceptance Criteria:**
- Show today's scheduled items/tasks
- Display time and description for each agenda item
- Mark completed items

#### Story 3: Take Knowledge Tests
As a user, I want to take tests on the knowledge I've acquired, so that I can assess my understanding and reinforce learning.

**Acceptance Criteria:**
- Access available tests/quizzes
- Answer questions and submit responses
- View test results and scores
- See areas for improvement

#### Story 4: Review Past Week's Learning Materials
As a user, I want to revisit and review learning materials from the past week, so that I can reinforce my knowledge and track my learning progress.

**Acceptance Criteria:**
- Filter/view materials from the past 7 days
- Search by category or topic
- Access full content of previously saved materials
- Sort by date or relevance

#### Story 5: Save and Organize Knowledge
As a user, I want to save, organize, and categorize information from various sources, so that I can build a centralized knowledge base for future reference.

**Acceptance Criteria:**
- Save articles, notes, and learning materials
- Categorize by topic/tag
- Search saved information
- Edit or delete saved items

## Proposed High-Level Design
1. **APIs** built in Go that create and manage data—these will be used by the LLM to populate the database
2. **Frontend** (technology-agnostic, focus on ease of use)
3. **Database** using PostgreSQL—chosen because the data structure is well-defined and consistent (news articles, agenda items, learning materials), making a relational database more suitable than a document-based approach
4. **Message Queue** to asynchronously handle writes to PostgreSQL

## Open Questions
1. How will the LLM validate information it adds to the app?
   - What validation mechanisms should be in place?
   - Should there be human review before information is persisted?
   - How do we ensure accuracy for technical content vs. news articles?

