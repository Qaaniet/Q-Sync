---
status: Active
progress: 5
---
# 🏛 Boudjie
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
- [ ] Gather resources
- [ ] Execute tasks
- [ ] Finish floor plans and 3D
- [ ] Send over presentation format

---
## ✅ Tasks
- [ ] Logo
- [ ] Character
- [ ] Artworks
- [ ] Floor plan
- [ ] 3D
- [ ] Sections
- [ ] Decor
- [ ] Programming branding that can find similar links

---
## 📝 Notes
The prompt: Highlighting all of the things that need to be done

>[!tip] use the branding created to generate floor plans and then just add dimensions

I am creating a branding prototype for a chicken shop. The name of the chicken shop is Boudjie. This is a cute way of saying chicken leg in South Africa. I have completed the typography logo for the brand and now want to create the finished results associated with what will be apart of the brand. I want to create a chicken mascot for the branding that I will animate in Adobe After Effects. There will also be various artworks and designs where this chicken mascot named Boudjie will appear, therefore consistency is highly important.

Alright lets begin. The first image needed to be looked at titled Boudjie 1 is the idea I want for the character Boudjie. I want you to keep the bean shaped body and just add the minimal characteristics of a chicken to it or the Character Logo and mascot.

The next image titled Boudjie 2 is the character doing various activities, this is crucial as it there needs to be variety in the character as he will eventually be animated and is also needed to illustrate various things like if the food is spicy he should cartoonishly show this by breathing fire for example.

The next image is titled the character template. This is the formatting I want Boudjie to be displayed as.

I want the character to almost look like iPhone emojis. Therefore I copied 3 images titled style 1,2 and 3 to help with the styling aspect of the finished design.



---
