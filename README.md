[index.html](https://github.com/user-attachments/files/26489773/index.html)
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>List Game dari Excel</title>
  <script src="https://cdn.jsdelivr.net/npm/xlsx/dist/xlsx.full.min.js"></script>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #0f172a;
      color: #fff;
      text-align: center;
      padding: 20px;
    }
    h1 {
      margin-bottom: 20px;
    }
    input {
      margin-bottom: 20px;
    }
    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 20px;
      background: #1e293b;
    }
    th, td {
      border: 1px solid #334155;
      padding: 10px;
    }
    th {
      background: #2563eb;
    }
    tr:hover {
      background: #334155;
    }
  </style>
</head>
<body>

<h1>📊 List Game dari File Excel</h1>

<input type="file" id="upload" accept=".xlsx, .xls" />

<div id="table-container"></div>

<script>
  document.getElementById('upload').addEventListener('change', function(e) {
    const file = e.target.files[0];
    const reader = new FileReader();

    reader.onload = function(e) {
      const data = new Uint8Array(e.target.result);
      const workbook = XLSX.read(data, { type: 'array' });
      const sheet = workbook.Sheets[workbook.SheetNames[0]];
      const html = XLSX.utils.sheet_to_html(sheet);
      document.getElementById('table-container').innerHTML = html;
    };

    reader.readAsArrayBuffer(file);
  });
</script>

</body>
</html>
