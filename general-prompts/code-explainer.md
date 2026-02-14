# Code Explainer

Understand code like you're debugging it.

---

## Prompt

```
Explain this code like I'm debugging it.

[paste code]

Include:
- what it does (high-level purpose)
- why each part exists
- likely failure points
- how to improve it
```

---

## Example Usage

```
Explain this code like I'm debugging it.

def process_orders(orders):
    total = 0
    for order in orders:
        total += order['price'] * order['quantity']
        if order['status'] == 'pending':
            send_notification(order['customer_email'])
    return total

Include:
- what it does (high-level purpose)
- why each part exists
- likely failure points
- how to improve it
```

---

## What You'll Get

**Purpose**: Calculates order total and notifies customers about pending orders

**Why each part**:
- Loop accumulates price * quantity
- If statement filters pending orders
- send_notification alerts customers

**Failure points**:
- KeyError if order missing 'price', 'quantity', 'status', or 'customer_email'
- Race condition if order status changes during loop
- Email failures not handled
- Mixing calculation with side effects

**Improvements**:
- Validate order structure first
- Separate calculation from notification
- Handle email errors
- Use order.get() with defaults
- Consider async for emails

---

## When to Use

- Understanding unfamiliar code
- Code review
- Debugging issues
- Learning from examples
- Refactoring legacy code
