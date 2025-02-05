# AMAQA: A Metadata-based QA Dataset for RAG Systems

## Overview
AMAQA is a high-quality, metadata-enriched Question-Answer dataset designed for Retrieval-Augmented Generation (RAG) systems. It contains about 1.1 million English Telegram messages collected from 26 public groups, enriched with their metadata, and 450 High quality Question-Answers.

## Repository Structure
- `data/` - Contains the full dataset, split into 10 `.ndjson` files.
- `AMAQA_QA.csv` - A CSV file containing Question-Answer pairs.

## Data Structure
Each `.ndjson` file contains multiple entries in the following format:

```json
{
  "text": "This is the text of the message",
  "metadata": {
    "date": "2024-07-28 00:00:00",
    "is_forwarded": false,
    "has_media": false,
    "was_edited": false,
    "reactions": "reactions": {
      "_": "MessageReactions",
      "reactions": [
        {
          "_": "Reaction",
          "emoji": "💯",
          "count": 2
        }
      ]
    },
    "reactions_count": 2,
    "chat_name": "This is the name of the group chat"
  },
  "ground_truth": {
    "toxicity": 0.013005874,
    "profanity": 0.013268576,
    "insult": 0.008044879,
    "identity_attack": 0.0029968263,
    "threat": 0.007029374,
    "emotion": "neutral",
    "topics": ["Topic1", "Topic2"]
  }
}
```

### Fields Description
- **text**: The message content.
- **metadata**:
  - `date`: Timestamp of the message.
  - `is_forwarded`: Boolean indicating if the message was forwarded.
  - `has_media`: Boolean indicating if the message contains media.
  - `was_edited`: Boolean indicating if the message was edited.
  - `reactions`: Contains a list of reactions to the message (if available), where each reaction includes: the emoji used for the reaction and the number of times this reaction was added.
  - `reactions_count`: Total count of reactions.
  - `chat_name`: Name of the chat where the message was posted.
- **ground_truth**:
  - `toxicity`: The probability that the content is considered toxic. Score provided by [Perspective API](https://perspectiveapi.com/).
  - `profanity`: The probability that the content contains profanity. Score provided by Perspective API.
  - `insult`: The probability that the content contains an insult. Score provided by Perspective API.
  - `identity_attack`: The probability that the content includes an identity attack. Score provided by Perspective API.
  - `threat`: The probability that the content is a threat. Score provided by Perspective API.
  - `emotion`: Emotion of the text.
  - `topics`: List of topics (if any).

## CSV File Structure (`AMAQA_QA.csv`)
The CSV file contains structured Question-Answer pairs with relevant document references.

| ID  | Question | Answer | Relevant Document |
|-----|----------|--------|------------------|
| 1   | What is truth? | Truth is... | Text of the message from which the answer is extracted |


## Ethical consideration

The data collection was conducted with care to include only information from public Telegram channels and groups, explicitly excluding personal data such as usernames, phone numbers, user IDs, and chat IDs. The process aligns with Telegram’s Terms of Service ([Telegram Terms of Service](https://telegram.org/tos/), accessed 2025-01-27) and Telegram API’s Terms of Service ([Telegram API Terms of Service](https://core.telegram.org/api/terms), accessed 2025-01-27), as neither prohibits the collection of public chat data. We have also taken care to avoid flooding the platform with excessive requests during data collection.

Furthermore, our research complies with the academic research exemptions outlined in Article 85 of the GDPR ([Article 85 GDPR](https://gdpr-text.com/read/article-85/), accessed 2025-01-27), which provide flexibility for processing publicly available data in the interest of freedom of expression and academic purposes. Since our work exclusively involves publicly accessible content and does not handle private user data, it qualifies for legitimate or public interest exemptions. 

Additionally, we follow the GDPR’s principle of data minimization by focusing solely on English textual content from public posts, ensuring that only the information necessary for our research objectives is processed ([Data protection under GDPR](https://europa.eu/youreurope/business/dealing-with-customers/dataprotection/data-protection-gdpr/index_en.htm), accessed 2025-01-27). Finally, as the dataset includes channels and groups that discuss controversial topics, it may contain some controversial messages.




