# Habit Tracker
[[Daily Notes Hub]] 

Start:: 2025-10-24
End:: 2026-10-24

```dataviewjs
const habits = ["Exercise", "Salah", "Obsidian", "Incognito"];
const startDate = dv.current().Start;
const endDate = dv.current().End;

const pages = dv.pages()
    .where(p => p.file.day && p.file.day >= dv.date(startDate) && p.file.day <= dv.date(endDate));

dv.table(["Date", ...habits], 
    pages.sort(p => p.file.day, 'desc') // <-- changed to 'desc'
    .map(p => {
        const row = [p.file.day.toISODate()];
        habits.forEach(habit => {
            const checked = p.file.tasks
                .where(t => t.text.includes(habit) && t.completed)
                .length > 0;
            row.push(checked ? "✅" : "❌");
        });
        return row;
    })
);
```