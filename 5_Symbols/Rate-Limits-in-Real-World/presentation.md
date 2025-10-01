---
marp: true
theme: default
style: |
  h1 {
    color: #007bff; /* blue */
  }
  h2 {
    color: #fd7e14; /* orange */
  }
---

# ⏱️ Rate Limits in Real World

---

## 🤔 Understanding Rate Limits

- **What are they?**
  - Restrictions on the number of API requests within a specific time.
- **Why do they exist?**
  - To prevent abuse, ensure fair usage, and maintain service stability.
- **Common Types**
  - 📈 Request Rate Limits (per second/minute/hour)
  - 💥 Burst Limits
  - QUOTA Quota Limits (per day/month)

---

## 🛠️ Rate Limit Handling Strategies

- **Exponential Backoff**: Increase delay between retries exponentially.
- **Retry Logic**: Automatically retry failed requests.
- **Rate Limit Detection**: Use response headers (`X-RateLimit-Remaining`, `Retry-After`) and status codes (`429 Too Many Requests`) to detect rate limits.

---

## 🧩 Implementation Patterns

- **Circuit Breaker**: Stop sending requests for a period of time after a certain number of failures.
- **Token Bucket**: A simple algorithm for rate limiting.
- **Sliding Window Counter**: A more advanced algorithm for rate limiting.

---

## 🚀 Advanced Techniques

- **Adaptive Rate Limiting**: Dynamically adjust the request rate based on API responses.
- **Priority-Based Rate Limiting**: Prioritize important requests.
- **Distributed Rate Limiting**: Coordinate rate limiting across multiple instances.

---

## 📊 Monitoring and Alerting

- **Key Metrics**: Request rate, rate limit hits, retry attempts, success rate.
- **Alerting Rules**: Set up alerts for high rate limit hit rates, circuit breaker open state, etc.
- **Dashboards**: Visualize rate limit metrics.

---

## 👍 Best Practices

- **Graceful Degradation**: Provide a degraded experience instead of failing completely.
- **Request Batching**: Combine multiple requests into a single one.
- **Environment-Based Configuration**: Use different rate limit settings for development, staging, and production.
- **Testing**: Test your rate limit handling logic.

---

## 🌐 Real-World Examples

- **Twitter API**: 300 requests per 15 minutes.
- **GitHub API**: 5000 requests per hour (authenticated).
- **Slack API**: 1+ request per minute.

---

## ✅ Conclusion

- Effective rate limit handling is crucial for building reliable n8n workflows.
- Implement retry logic, exponential backoff, and monitoring to build resilient systems.
