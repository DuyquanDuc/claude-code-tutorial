# export-data

Add functionality to export study commit data.

## Instructions

When the user asks to add data export:

1. Add an export button to the UI near the stats section
2. Implement export in JSON format (raw data) or CSV format (date, message)
3. Use the Blob API and create a download link:

```javascript
function exportData(format) {
  const commits = getCommits();
  let content, filename, type;

  if (format === 'json') {
    content = JSON.stringify(commits, null, 2);
    filename = 'study-commits.json';
    type = 'application/json';
  } else {
    content = 'date,message\n' + commits.map(c =>
      `${c.date},"${c.message.replace(/"/g, '""')}"`
    ).join('\n');
    filename = 'study-commits.csv';
    type = 'text/csv';
  }

  const blob = new Blob([content], { type });
  const url = URL.createObjectURL(blob);
  const a = document.createElement('a');
  a.href = url;
  a.download = filename;
  a.click();
  URL.revokeObjectURL(url);
}
```
