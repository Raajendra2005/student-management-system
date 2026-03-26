<!DOCTYPE html>
<html>
<head>
    <title>Student Management System</title>
    <style>
        body {
            font-family: Arial;
            background: #f4f4f4;
            text-align: center;
        }
        h1 {
            background: #333;
            color: white;
            padding: 10px;
        }
        .container {
            width: 80%;
            margin: auto;
            background: white;
            padding: 20px;
            box-shadow: 0px 0px 10px gray;
        }
        input {
            padding: 10px;
            margin: 5px;
        }
        button {
            padding: 10px 15px;
            background: blue;
            color: white;
            border: none;
            cursor: pointer;
        }
        table {
            width: 100%;
            margin-top: 20px;
            border-collapse: collapse;
        }
        table, th, td {
            border: 1px solid black;
        }
        th {
            background: #333;
            color: white;
        }
    </style>
</head>

<body>

<h1>Student Management System</h1>

<div class="container">
    <h2>Add Student</h2>
    
    <input type="text" id="name" placeholder="Enter Name">
    <input type="text" id="class" placeholder="Enter Class">
    <input type="number" id="marks" placeholder="Enter Marks">
    
    <button onclick="addStudent()">Add Student</button>

    <h2>Student List</h2>
    
    <table id="studentTable">
        <tr>
            <th>Name</th>
            <th>Class</th>
            <th>Marks</th>
            <th>Action</th>
        </tr>
    </table>
</div>

<script>
    let students = [];

    function addStudent() {
        let name = document.getElementById("name").value;
        let studentClass = document.getElementById("class").value;
        let marks = document.getElementById("marks").value;

        if(name === "" || studentClass === "" || marks === "") {
            alert("Please fill all fields");
            return;
        }

        let student = { name, studentClass, marks };
        students.push(student);

        displayStudents();

        document.getElementById("name").value = "";
        document.getElementById("class").value = "";
        document.getElementById("marks").value = "";
    }

    function displayStudents() {
        let table = document.getElementById("studentTable");

        table.innerHTML = `
        <tr>
            <th>Name</th>
            <th>Class</th>
            <th>Marks</th>
            <th>Action</th>
        </tr>`;

        students.forEach((s, index) => {
            table.innerHTML += `
            <tr>
                <td>${s.name}</td>
                <td>${s.studentClass}</td>
                <td>${s.marks}</td>
                <td>
                    <button onclick="deleteStudent(${index})">Delete</button>
                </td>
            </tr>`;
        });
    }

    function deleteStudent(index) {
        students.splice(index, 1);
        displayStudents();
    }
</script>

</body>
</html>
