# Token Optimization: Middle-man Projection

To handle the massive JSON from `getLoanAccounts` and save tokens, we use a **Projection Logic** in the Yellow.ai Workflow.

## The Problem
The API returns 15+ fields per account (e.g., `internal_bank_code`, `audit_date`, `risk_score`), but the LLM only needs `loan_id`, `type`, and `tenure` to display the cards.

## The Solution: JSON Projection
In the Yellow.ai **API Node** or a subsequent **Function Node**, apply the following transformation before passing the data to the LLM or DRM:

### Function Node Logic (JavaScript)
```javascript
// Assume 'apiResponse' is the raw data from the getLoanAccounts API
const rawAccounts = apiResponse.accounts;

// Projection: Keep only what's needed for the UI
const projectedAccounts = rawAccounts.map(acc => ({
    loan_id: acc.loan_id,
    type: acc.type,
    tenure: acc.tenure
}));

// Return the optimized object
return { accounts: projectedAccounts };
```

## Benefits
1. **Token Savings**: Reduces the payload size by ~80%, preventing token limit issues.
2. **Hallucination Prevention**: By removing internal codes and audit dates, the LLM won't accidentally mention them to the user.
3. **Speed**: Smaller payloads result in faster processing by the LLM.
