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

# 🌦️ Practical Real-World Projects

Daily Weather Report

---

## 🎯 Objective

Create a workflow that automatically sends a daily weather report to your email every morning.

---

## 🤖 The Demo Workflow

`daily-weather-report-workflow.json`

This workflow demonstrates a simple, practical use case for n8n:

1.  **Cron Trigger**: Runs every day at 8 AM.
2.  **HTTP Request**: Gets weather data from a public API.
3.  **Set**: Formats the weather data into a readable message.
4.  **Email**: Sends the formatted weather report to your email address.

---

## 🔧 How it Works

<div class="columns">
<div>

### 1. Get Weather Data

- The workflow uses a free weather API to get the forecast.
- You can customize the location to get weather for your city.

</div>
<div>

### 2. Format the Report

- The `Set` node creates an HTML-formatted email body.
- It includes temperature, conditions, and a weather icon.

</div>
</div>

---

## ✅ Best Practices

- Use **credentials** to store your API keys securely.
- Add **error handling** to catch API failures.
- **Customize the schedule** to fit your needs.

---

## 📚 External Resources

- **OpenWeatherMap API**: [https://openweathermap.org/api](https://openweathermap.org/api)
- **n8n Cron Node Documentation**: [https://docs.n8n.io/nodes/n8n-nodes-base.cron/](https://docs.n8n.io/nodes/n8n-nodes-base.cron/)