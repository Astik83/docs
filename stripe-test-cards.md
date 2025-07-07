# Stripe Test Card Numbers

Test payment scenarios for Stripe integration. Use these cards in **test mode only**.

## ✅ Successful Payments

| Card Type          | Card Number           | Expiry | CVC  | ZIP     | Result          |
|--------------------|-----------------------|--------|------|---------|-----------------|
| Basic Visa         | `4242 4242 4242 4242` | Any future | Any | Any | ✅ Success      |
| Debit Card         | `4000 0566 5566 5556` | Any future | Any | Any | ✅ Success      |
| Mastercard         | `5555 5555 5555 4444` | Any future | Any | Any | ✅ Success      |
| Amex               | `3782 822463 10005`   | Any future | Any | Any | ✅ Success      |

## ❌ Payment Failures

| Failure Type               | Card Number           | Description                     |
|----------------------------|-----------------------|---------------------------------|
| Generic decline            | `4000 0000 0000 0002` | General purpose decline         |
| Insufficient funds         | `4000 0000 0000 9995` | Transaction exceeds balance     |
| Lost card                  | `4000 0000 0000 9987` | Card reported lost              |
| Stolen card                | `4000 0000 0000 9979` | Card reported stolen            |
| Expired card               | `4000 0000 0000 0069` | Card expiration date passed     |
| Incorrect CVC              | `4000 0000 0000 0127` | Wrong security code entered     |
| Processing error           | `4000 0000 0000 0119` | Bank processing failure         |
| Fraudulent transaction     | `4100 0000 0000 0019` | Blocked by fraud detection      |

## 🔐 3D Secure Authentication

| Scenario          | Card Number           | Authentication Result | Payment Result |
|-------------------|-----------------------|------------------------|----------------|
| 3D Secure success | `4000 0027 6000 3184` | ✅ Authenticated       | ✅ Success     |
| 3D Secure failure | `4000 0025 0000 3155` | ❌ Failed              | ❌ Declined    |
| 3D Secure required| `4000 0025 0000 3155` | Requires authentication| Pending        |

## 🌍 Regional Cards

| Country       | Card Type          | Card Number           | Result          |
|---------------|--------------------|-----------------------|-----------------|
| US            | Visa               | `4000 0035 6000 0008`| ✅ Success      |
| UK            | Mastercard         | `5555 5586 1000 0001`| ✅ Success      |
| IN (India)    | Visa               | `4000 0035 6000 0008`| ✅ Success      |
| AU (Australia)| Amex               | `3700 0000 0000 002` | ✅ Success      |
| Blocked       | Restricted country | `4000 0038 0000 0000`| ❌ Declined     |

## 🧪 Usage Tips

1. **Expiry Date**: Any future date (e.g., `12/34`)
2. **CVC**: Any 3-digit number
3. **ZIP/Postal Code**: Any valid code
4. **Test Mode**: Works only in Stripe test environment
5. **Authentication**: 
   - Use `4242424242424242` for simple payments
   - Use `4000002500003155` for 3D Secure flow testing
6. **Special Cards**:
   - `4000 0000 0000 3220` - Charge will be blocked as fraudulent
   - `4000 0000 0000 3087` - Disputed payment scenario

## 💡 Example Payments

```javascript
// Successful payment
const testCard = {
  number: '4242424242424242',
  exp: '12/34',
  cvc: '123',
  zip: '560001'
};

// 3D Secure flow
const threeDSecureCard = {
  number: '4000002500003155',
  exp: '12/34',
  cvc: '123'
};