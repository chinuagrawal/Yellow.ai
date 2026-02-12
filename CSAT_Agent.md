# CSAT Agent Design

This agent is triggered when the user clicks "Rate our chat" in the Loan Details view.

## 1. Objective

Collect a rating and qualitative feedback from the user.

## 2. Conversation Flow

1. **Greeting**: "We value your feedback! How would you rate your experience today?"
2. **Rating Collection (Quick Replies)**:
   - **Good** (Value: 3)
   - **Average** (Value: 2)
   - **Bad** (Value: 1)
3. **Feedback Collection**:
   - If "Bad": "We're sorry to hear that. Could you tell us what we can do better?"
   - If "Good/Average": "Thank you! Is there anything else you'd like to share?"
4. **Closing**: "Thank you for your feedback! Have a great day with Yellow Bank."

## 3. Data Storage

Store the results in a "CSAT_Logs" database table with the following columns:

- `user_id` (Phone Number)
- `rating` (Good/Average/Bad)
- `feedback` (Text)
- `timestamp` (Date/Time)
