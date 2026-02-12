# Dynamic Rich Media (DRM) Templates

## 1. getLoanAccounts DRM (Interactive Cards)
This DRM displays the list of loans. Each card has a "Select" button that sends the `loan_id` as a message.

**Template Structure**:
```json
{
  "type": "carousel",
  "cards": [
    {
      "title": "{{type}}",
      "subtitle": "Loan ID: {{loan_id}}\nTenure: {{tenure}}",
      "actions": [
        {
          "title": "Select",
          "type": "postback",
          "payload": "Select {{loan_id}}"
        }
      ]
    }
  ]
}
```

## 2. loanDetails DRM (Quick Replies)
This DRM displays the specific details of the selected loan and includes the CSAT trigger.

**Template Structure**:
```json
{
  "type": "text",
  "text": "Here are your details for Loan {{account_id}}:\n\n- Interest Rate: {{interest_rate}}\n- Principal Pending: {{principal_pending}}\n- Interest Pending: {{interest_pending}}\n- Nominee: {{nominee}}\n- Tenure: {{tenure}}",
  "quickReplies": [
    {
      "title": "Rate our chat",
      "type": "postback",
      "payload": "trigger_csat"
    }
  ]
}
```
*Note: The "Rate our chat" button directs the user to the CSAT agent flow.*
