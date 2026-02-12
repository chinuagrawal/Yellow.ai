# Edge Case & Language Logic

## 1. "Old Number" / "Different Number" Reset
**Scenario**: User says "Wait, that's my old number" or "I want to check for a different number".

**Logic (Yellow.ai Node Configuration)**:
- Create an **Intent/Expression** to catch phrases like "old number", "different number", "change number".
- When triggered:
    1. **Clear Variables**: Set `phone_number` and `dob` to `null`.
    2. **Message**: "I understand. Let's restart the verification with your correct details."
    3. **Jump to Node**: Send the user back to the "Request Phone Number" node.
    4. **Maintain Intent**: Ensure the `view_loan_details` context is still active so the bot doesn't ask "How can I help you?" again.

## 2. Language Restriction
**Constraint**: English Only.

**Logic**:
- In the **Global Model / System Prompt**, add a strict instruction.
- **Implementation**:
    - Use the "Language Detection" feature if available, or rely on the LLM's system prompt.
    - If non-English input is detected, trigger a "Language Not Supported" flow.
    - Response: "I apologize, but I am restricted to operating in English only. How can I help you in English today?"

## 3. Failure Scenarios
- **Incorrect OTP**:
    - Variable `otp_attempts` (default 0).
    - If user OTP != workflow OTP:
        - `otp_attempts += 1`.
        - If `otp_attempts < 3`: "Incorrect OTP. Please try again. (Attempts left: {{3 - otp_attempts}})"
        - If `otp_attempts >= 3`: "Too many incorrect attempts. For security, we must restart the verification." -> Clear slots -> Reset flow.
- **API Failures**:
    - If workflow status != `success`: "Our systems are currently under maintenance. Please try again later."
