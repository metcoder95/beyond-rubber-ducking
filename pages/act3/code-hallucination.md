# Real Hallucination Example

```javascript {1|3-12|14-17|6}
// Prompt: "Apply discount if user has loyalty points AND cart > $50"

// AI Response (WRONG - business logic flaw):
function applyDiscount(cart, user) {
  const discount = 0.1;
  if (user.loyaltyPoints > 0 || cart.total > 50) {
    cart.total = cart.total * (1 - discount);
  }
  return cart;
}

// ... more code

// Problem: Uses OR instead of AND
// - Any user with points gets discount, even on $1 purchase
// - Any $51 purchase gets discount, even without points
// Should be: user.loyaltyPoints > 0 && cart.total > 50
```
