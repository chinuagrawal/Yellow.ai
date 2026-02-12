# Yellow Bank - Mock API Definitions (Beeceptor)

These endpoints should be configured in your Beeceptor dashboard.

## 1. Trigger OTP
**Endpoint**: `POST /api/v1/triggerOTP`
**Payload**:
```json
{
  "status": "success",
  "otp": 1234, 
  "message": "OTP sent successfully"
}
```
*Note: Randomly return one of [1234, 5678, 7889, 1209] using Beeceptor's rules or just hardcode one for testing.*

## 2. Get Loan Accounts (Workflow A)
**Endpoint**: `GET /api/v1/getLoanAccounts?phone={phone}`
**Response (Massive JSON for Token Optimization test)**:
```json
{
  "accounts": [
    {
      "loan_id": "L-99812",
      "type": "Home Loan",
      "tenure": "15 Years",
      "internal_bank_code": "HB-X99",
      "audit_date": "2024-01-01",
      "branch_id": "BR-001",
      "manager_id": "M-55",
      "risk_score": "A+",
      "collateral_type": "Property",
      "insurance_status": "Active",
      "last_payment_date": "2024-02-01",
      "next_audit": "2025-01-01",
      "legacy_system_id": "LEG-123",
      "region": "North",
      "tax_id": "TX-991"
    },
    {
      "loan_id": "L-11223",
      "type": "Car Loan",
      "tenure": "5 Years",
      "internal_bank_code": "CB-Y22",
      "audit_date": "2023-12-01",
      "branch_id": "BR-005",
      "manager_id": "M-12",
      "risk_score": "B",
      "collateral_type": "Vehicle",
      "insurance_status": "Active",
      "last_payment_date": "2024-01-15",
      "next_audit": "2024-12-01",
      "legacy_system_id": "LEG-456",
      "region": "South",
      "tax_id": "TX-882"
    }
  ]
}
```

## 3. Loan Details (Workflow B)
**Endpoint**: `GET /api/v1/loanDetails?account_id={account_id}`
**Response**:
```json
{
  "account_id": "L-99812",
  "tenure": "15 Years",
  "interest_rate": "8.5%",
  "principal_pending": "₹45,00,000",
  "interest_pending": "₹1,20,000",
  "nominee": "Anjali Sharma",
  "status": "Active"
}
```
