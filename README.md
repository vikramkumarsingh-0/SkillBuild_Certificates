"# SkillBuild_Certificates" 
<!DOCTYPE html>
<html>
  <head>
    <title>Excel File Viewer</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/openpyxl/3.0.9/openpyxl.min.css">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/openpyxl/3.0.9/openpyxl.min.js"></script>
  </head>
  <body>
    <div id="excel-viewer"></div>
    <script>
      // Replace 'your_excel_file.xlsx' with the actual path to your Excel file
      var excelFilePath = 'your_excel_file.xlsx';

      // Use Openpyxl to load and render the Excel file
      Openpyxl.load(excelFilePath, function(error, workbook) {
        if (error) {
          console.error('Error loading Excel file:', error);
        } else {
          var sheet = workbook.sheets[0]; // Assuming you want to display the first sheet
          var tableHTML = '<table>';
          for (var row in sheet.rows) {
            if (row !== 'header') {
              tableHTML += '<tr>';
              for (var cell in sheet.rows[row]) {
                tableHTML += '<td>' + sheet.rows[row][cell] + '</td>';
              }
              tableHTML += '</tr>';
            }
          }
          tableHTML += '</table>';
          document.getElementById('excel-viewer').innerHTML = tableHTML;
        }
      });
    </script>
  </body>
</html>
