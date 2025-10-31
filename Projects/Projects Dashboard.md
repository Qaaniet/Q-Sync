
# 🚀 Projects Dashboard

---

## 🔥 Active Projects
| Project                | Status         | Priority | Deadline    |
| ---------------------- | -------------- | -------- | ----------- |
| Music Player App       | 🟡 In Progress | Medium   | Nov 15      |
| Obsidian Customization | 🟢 Completed   | High     | 2025 Oct 25 |
| Steam Integration      | 🔵 Planned     | Low      | Dec 10      |
| BAT Gina               | 🟢 Completed   | High     | 2025 Oct 29 |
|                        | 🔴 Idea        |          |             |

```dataviewjs
const statuses = ["All", "Active", "Completed", "On Hold"];
let selectedStatus = "All";

dv.header(1, "📂 Projects Dashboard");

// Dropdown
const select = document.createElement("select");
statuses.forEach(status => {
    const option = document.createElement("option");
    option.value = status;
    option.textContent = status;
    select.appendChild(option);
});
select.value = selectedStatus;
select.style.marginBottom = "10px";
dv.container.appendChild(select);

// Table container
const tableContainer = document.createElement("div");
dv.container.appendChild(tableContainer);

function render(statusFilter) {
    tableContainer.innerHTML = "";

    let pages = dv.pages("#project").sort(p => p.file.ctime, 'desc');
    if (statusFilter !== "All") {
        pages = pages.filter(p => (p.status || "Active") === statusFilter);
    }

    if (pages.length === 0) {
        tableContainer.innerHTML = "<p><em>No projects found.</em></p>";
        return;
    }

    const table = document.createElement("table");
    table.style.width = "100%";
    table.style.borderCollapse = "collapse";

    const headerRow = document.createElement("tr");
    ["Project", "Status", "Progress", "Last Updated"].forEach(h => {
        const th = document.createElement("th");
        th.textContent = h;
        th.style.borderBottom = "2px solid #ccc";
        th.style.padding = "6px";
        th.style.textAlign = "left";
        headerRow.appendChild(th);
    });
    table.appendChild(headerRow);

    pages.forEach(p => {
        const row = document.createElement("tr");

        // Project name as clickable link
        const projectCell = document.createElement("td");
        const link = document.createElement("a");
        link.href = p.file.path;
        link.textContent = p.file.name;
        link.style.color = "#0077cc";
        link.style.textDecoration = "none";
        link.onclick = (e) => {
            e.preventDefault();
            app.workspace.openLinkText(p.file.path, '', false);
        };
        projectCell.appendChild(link);
        row.appendChild(projectCell);

        // Status
        const statusCell = document.createElement("td");
        const status = p.status || "Active";
        statusCell.textContent = status;
        statusCell.style.color = status === "Completed" ? "green" :
                                 status === "On Hold" ? "orange" : "blue";
        row.appendChild(statusCell);

        // Progress bar
        const progressCell = document.createElement("td");
        const progress = p.progress || 0;
        const bar = document.createElement("div");
        bar.style.width = "100%";
        bar.style.background = "#eee";
        bar.style.borderRadius = "4px";
        bar.style.overflow = "hidden";
        const fill = document.createElement("div");
        fill.style.width = `${progress}%`;
        fill.style.height = "10px";
        fill.style.background = progress === 100 ? "green" : "#4cafef";
        bar.appendChild(fill);
        progressCell.appendChild(bar);
        row.appendChild(progressCell);

        // Last updated
        const updatedCell = document.createElement("td");
        updatedCell.textContent = p.file.mtime.toFormat("yyyy-MM-dd");
        row.appendChild(updatedCell);

        table.appendChild(row);
    });

    tableContainer.appendChild(table);
}

select.onchange = () => render(select.value);
render(selectedStatus);
```
