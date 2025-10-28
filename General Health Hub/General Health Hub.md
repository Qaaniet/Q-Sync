## General Health Hub

```dataviewjs
let selected = "All"; // Default is now "See All"
const categories = ["Routine", "Meals", "Exercise", "Events"];

dv.header(1, "📚 General Health Hub");

// Create dropdown
const select = document.createElement("select");
categories.forEach(cat => {
    const option = document.createElement("option");
    option.value = cat;
    option.textContent = cat;
    select.appendChild(option);
});
const allOption = document.createElement("option");
allOption.value = "All";
allOption.textContent = "See All";
select.appendChild(allOption);
select.value = selected;

// Append dropdown
dv.container.appendChild(select);

// Render function
function render(category) {
    // Clear old tables
    dv.container.querySelectorAll("table, h2, p").forEach(el => el.remove());

    if (category === "All") {
        categories.forEach(cat => {
            dv.header(2, cat);
            let pages = dv.pages(`#hub/health and #category/${cat.toLowerCase()}`).sort(p => p.file.ctime, 'desc');
            if (pages.length === 0) {
                dv.paragraph("_No notes yet in this category._");
            } else {
                dv.table(["Title", "Created", "Modified"],
                    pages.map(p => [
                        dv.fileLink(p.file.path),
                        p.file.ctime.toFormat("yyyy-MM-dd"),
                        p.file.mtime.toFormat("yyyy-MM-dd")
                    ])
                );
            }
        });
    } else {
        dv.header(2, `Showing: ${category}`);
        let pages = dv.pages(`#hub/health and #category/${category.toLowerCase()}`).sort(p => p.file.ctime, 'desc');
        if (pages.length === 0) {
            dv.paragraph("_No notes yet in this category._");
        } else {
            dv.table(["Title", "Created", "Modified"],
                pages.map(p => [
                    dv.fileLink(p.file.path),
                    p.file.ctime.toFormat("yyyy-MM-dd"),
                    p.file.mtime.toFormat("yyyy-MM-dd")
                ])
            );
        }
    }
}

// Dropdown change event
select.onchange = () => {
    render(select.value);
};

// Initial render
render(selected);
```
