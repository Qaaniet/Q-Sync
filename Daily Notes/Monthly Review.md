
# 📆 Monthly Review
[[Daily Notes Hub]]  

Month:: 10
Year:: 2025
```dataviewjs
// Read month and year from inline fields
const targetMonth = parseInt(dv.current().Month);
const targetYear = parseInt(dv.current().Year);

// Collect tasks with their parent page date
let tasks = dv.pages("#daily")
    .where(p => p.file.day && p.file.day.month === targetMonth && p.file.day.year === targetYear)
    .flatMap(p => p.file.tasks.map(t => {
        const [year, month, day] = p.file.name.split("-").map(Number);
        const dateObj = new Date(year, month - 1, day); // JS Date
        return {
            text: t.text,
            completed: t.completed,
            section: t.section,
            date: dateObj,
            filename: p.file.name
        };
    }))
    .filter(t => {
        const sectionName = String(t.section || "").toLowerCase();
        return t.text && t.text.length > 0 && !sectionName.includes("habits");
    });

// Sort by most recent date
tasks.sort((a, b) => b.date - a.date);

const completed = tasks.filter(t => t.completed);
const incomplete = tasks.filter(t => !t.completed);

dv.header(4, `❌ Incomplete Tasks for ${targetYear}-${String(targetMonth).padStart(2, '0')}`);
dv.table(["Task", "Date"], incomplete.map(t => [t.text, t.filename]));

dv.header(4, `✅ Completed Tasks for ${targetYear}-${String(targetMonth).padStart(2, '0')}`);
dv.table(["Task", "Date"], completed.map(t => [t.text, t.filename]));
``
```