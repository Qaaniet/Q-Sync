---
status: Active
progress: 50
---
# 🏛 Qwaanify
[[Projects Dashboard]] #project

---
## 🎯 Project Overview
**Project Name:** Boudjie Chicken Shop
**Client:** [Client Name]  
**Deadline:** Dec 15, 2025  
**Status:** 🟢 In Progress  
```button
name Project File
type link
action file:///F:\Work\Chicken Shop
class folder-button
```
---
```dataviewjs
const tasks = dv.current().file.tasks;
const total = tasks.length;
const done = tasks.filter(t => t.completed).length;
const percent = total === 0 ? 0 : Math.round((done / total) * 100);

// Display progress visually
const progressEl = document.createElement("div");
progressEl.style.margin = "10px 0";
progressEl.style.fontWeight = "bold";
progressEl.textContent = `Progress: ${percent}% (${done}/${total} tasks)`;

const bar = document.createElement("div");
bar.style.width = "100%";
bar.style.background = "#eee";
bar.style.borderRadius = "4px";
bar.style.overflow = "hidden";
const fill = document.createElement("div");
fill.style.width = `${percent}%`;
fill.style.height = "10px";
fill.style.background = percent === 100 ? "green" : "#4cafef";
bar.appendChild(fill);

dv.container.appendChild(progressEl);
dv.container.appendChild(bar);
````

## ✅ Goals
- [x] Define scope
- [x] Gather resources
- [x] Execute tasks

---
## ✅ Tasks
- [ ] Task 1
- [ ] Task 2
- [ ] Task 3

---
## 📝 Notes
Add your notes here...

---
