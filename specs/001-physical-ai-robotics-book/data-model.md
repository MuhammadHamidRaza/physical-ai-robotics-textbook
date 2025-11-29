# Data Model: Physical AI & Humanoid Robotics Textbook

## Entities

### Book Content
- **Description**: The core content of the textbook, organized into chapters and sections.
- **Attributes**:
  - `id`: Unique identifier for each content unit (e.g., chapter, section, paragraph).
  - `text`: The textual content.
  - `language`: Original language of the content (e.g., 'en').
  - `metadata`: Any associated metadata (e.g., author, publication date, version).
  - `vector_embedding`: Numerical representation for RAG queries (stored in Qdrant).

### User
- **Description**: An individual interacting with the book and chatbot.
- **Attributes**:
  - `auth_id`: Unique identifier from Better-Auth (for authentication).
  - `local_profile_id`: Unique identifier for the local user profile.
  - `software_background`: User's software experience (collected at signup).
  - `hardware_background`: User's hardware experience (collected at signup).
- **Relationships**:
  - One-to-one with `Local User Profile` (via `local_profile_id`).

### Query
- **Description**: User's input to the RAG chatbot.
- **Attributes**:
  - `text`: The query string.
  - `context_text`: Optional text selected by the user for contextualized queries.
  - `timestamp`: Time of the query.
  - `user_id`: Identifier of the user making the query.

### Chatbot Response
- **Description**: AI-generated answer to a user query.
- **Attributes**:
  - `response_text`: The generated answer.
  - `source_content_ids`: References to `Book Content` units used to generate the response.
  - `query_id`: Identifier of the query this response corresponds to.
  - `timestamp`: Time of the response.

### Personalization Settings
- **Description**: User-specific preferences for content display, stored locally.
- **Attributes**:
  - `setting_name`: Name of the personalization setting (e.g., 'font_size', 'difficulty_level').
  - `setting_value`: Value of the setting.
  - `user_profile_id`: Links to the `Local User Profile`.

### Translation Data
- **Description**: Content translated into Urdu.
- **Attributes**:
  - `original_content_id`: Reference to the `Book Content` unit.
  - `translated_text`: The content in Urdu.
  - `target_language`: 'ur' (Urdu).
  - `translated_by`: (Optional) Agent or user who initiated translation.

### Local User Profile
- **Description**: Stores personalization settings and data for a user, managed independently of Better-Auth.
- **Attributes**:
  - `id`: Unique identifier for the local profile.
  - `user_auth_id`: Linked to `User`'s `auth_id` for association.
  - `personalization_settings`: Collection of `Personalization Settings`.
  - `last_active_chapter`: Tracks the user's last viewed chapter.
