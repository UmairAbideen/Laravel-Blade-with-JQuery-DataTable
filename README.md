# Laravel-Blade-with-JQuery-DataTable
This project demonstrates a simple integration of **Laravel Blade** with **DataTables** to display paginated and searchable employee data in a table.

## 🚀 Features

- Display employee data in a table
- Pagination (default 5 rows)
- Column sorting
- Search/filter functionality
- Uses DataTables CDN (no local asset setup needed)

## 🛠️ Tech Stack

| Layer     | Technology         |
|-----------|--------------------|
| Backend   | Laravel Blade      |
| Frontend  | Bootstrap 5        |
| Table UI  | DataTables jQuery  |
| Language  | PHP, HTML, JavaScript |

## 💡 Concept

DataTables is a lightweight and powerful jQuery plugin for rendering HTML tables with rich UI functionality — like pagination, searching, and sorting. This snippet uses DataTables via CDN and shows how you can loop over backend data (`$employees`) from Laravel in a Blade template.

---

## 📄 Sample Code

```blade
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Employee Table</title>
    <link rel="stylesheet" href="https://cdn.datatables.net/1.13.6/css/jquery.dataTables.min.css">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css">
</head>
<body class="p-4">

<div class="container">
    <h2 class="mb-4">Employee List</h2>

    <table id="employeeTable" class="display table table-bordered">
        <thead>
            <tr>
                <th>ID</th>
                <th>Name</th>
                <th>Email</th>
                <th>Position</th>
                <th>Age</th>
            </tr>
        </thead>
        <tbody>
            @foreach ($employees as $employee)
                <tr>
                    <td>{{ $employee->id }}</td>
                    <td>{{ $employee->name }}</td>
                    <td>{{ $employee->email }}</td>
                    <td>{{ $employee->position }}</td>
                    <td>{{ $employee->age }}</td>
                </tr>
            @endforeach
        </tbody>
    </table>
</div>

<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<script src="https://cdn.datatables.net/1.13.6/js/jquery.dataTables.min.js"></script>

<script>
    $(document).ready(function() {
        $('#employeeTable').DataTable({
            "pageLength": 5
        });
    });
</script>
</body>
</html>

```

# Employee Controller
public function index() {
    $employees = Employee::all();
    return view('your-view-name', compact('employees'));
}

# When to Use
Perfect for dashboards, admin panels, and internal tools where you need a quick and responsive way to view database records.
