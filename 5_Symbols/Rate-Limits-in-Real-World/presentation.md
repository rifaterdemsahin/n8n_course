---
marp: true
theme: uncover
style: |
  .columns {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 1rem;
  }
  h1, h2, h3, h4, h5, h6 {
    color: #0277b5;
  }
  a {
    color: #f89d21;
  }
  strong {
    color: #f89d21;
  }
---

# ⏳ Handling Rate Limits

Building resilient workflows.

---

## 🤔 What are Rate Limits?

APIs use rate limits to control how many requests you can make in a certain amount of time. If you exceed the limit, you'll get an error (usually a `429 Too Many Requests` status code).

---

## 🛠️ Strategies for Handling Rate Limits

<div class="columns">
<div>

### Exponential Backoff

- If a request fails, wait for a short time and then retry.
- Double the waiting time after each failed attempt.

</div>
<div>

### Retry Logic

- Only retry on specific errors (like `429` or `503`).
- Don't retry on errors that won't be fixed by waiting (like `401 Unauthorized`).

</div>
</div>

---

## 🤖 The Demo Workflow

`rate-limit-handling-workflow.json`

This workflow demonstrates how to handle rate limits:

1.  **Set Config**: Defines max retries and delay times.
2.  **Make API Request**: Tries to call an API.
3.  **Check for 429 Error**: If a rate limit error occurs, it enters the retry loop.
4.  **Exponential Backoff**: Calculates how long to wait before the next retry.
5.  **Wait**: Pauses the workflow.
6.  **Loop**: Goes back to the API request until it succeeds or runs out of retries.

---

## ✅ Best Practices

- **Read the API documentation** to understand the rate limits.
- Use **exponential backoff** to avoid overwhelming the API.
- **Check response headers** like `X-RateLimit-Remaining` and `Retry-After`.
- Use a **Circuit Breaker** pattern for more advanced scenarios.

---

## 📚 External Resources

- **n8n Error Handling Documentation**: [https://docs.n8n.io/error-handling/](https://docs.n8n.io/error-handling/)
- **Stripe's Article on Rate Limiters**: [https://stripe.com/blog/rate-limiters](https://stripe.com/blog/rate-limiters)