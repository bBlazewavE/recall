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
As a user, I want to open this app every morning to view the latest updates from the Python and programming communities (such as news from Y Combinator). I also want to see my daily agenda and take tests on the knowledge I've acquired. Additionally, I want a view to revisit and review learning materials from the past week.

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

