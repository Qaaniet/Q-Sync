# 🏠 My Life Library
  
Welcome to the hub of everything I learn, apply, and track.

---

> [!info] **🔥 Quick Access**

- [[Monthly Review]]
- [[General Health Hub]]
- [[Philosophy Hub]]
- [[Tech Hub]]
- [[Knowledge Library]]
- [[Projects Dashboard]]
- [[Wishlist]]
---
## 📊 Monthly Overview

```dataviewjs

const tasks = dv.pages("#daily").file.tasks;

const total = tasks.length;

const completed = tasks.where(t => t.completed).length;

const percent = total ? Math.round((completed / total) * 100) : 0;

  

dv.header(3, "✅ Weekly Task Progress");

dv.paragraph(`Progress: ${percent}%`);

dv.paragraph("[" + "█".repeat(percent / 10) + "░".repeat(10 - percent / 10) + "]");
```
