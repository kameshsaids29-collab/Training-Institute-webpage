<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ABC Training Institute</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:Arial, sans-serif;
}

body{
    background:#f4f4f4;
}

/* Header */
header{
    background:#0077cc;
    color:white;
    text-align:center;
    padding:20px;
}

/* Navigation */
nav{
    background:#01060a;
}

nav ul{
    list-style:none;
    display:flex;
    justify-content:center;
}

nav ul li{
    padding:15px 20px;
}

nav ul li a{
    color:white;
    text-decoration:none;
}

nav ul li:hover{
    background:white;
}

/* Container */
.container{
    width:90%;
    max-width:900px;
    margin:20px auto;
}

/* Card */
.card{
    background:white;
    padding:20px;
    border-radius:10px;
    box-shadow:0 0 10px rgba(0,0,0,0.2);
    margin-bottom:30px;
}

.card h2{
    text-align:center;
    color:white;
    margin-bottom:20px;
}

.form-group{
    margin-bottom:15px;
}

label{
    display:block;
    margin-bottom:5px;
    font-weight:bold;
}

input,
select,
textarea{
    width:100%;
    padding:10px;
    border:1px solid #ccc;
    border-radius:5px;
}

.gender,
.skills{
    display:flex;
    gap:15px;
    flex-wrap:wrap;
}

.gender label,
.skills label{
    font-weight:normal;
}

button{
    padding:10px 20px;
    border:none;
    border-radius:5px;
    color:white;
    cursor:pointer;
    font-size:16px;
}



</style>
</head>

<body>

<header>
<h1>ABC Training Institute</h1>
</header>

<nav>
<ul>
<li><a href="#">Home</a></li>
<li><a href="#">Courses</a></li>
<li><a href="#">Register</a></li>
<li><a href="#">Contact</a></li>
</ul>
</nav>

<div class="container">

<div class="card">

<h2>Student Registration Form</h2>

<form id="registrationForm">

<div class="form-group">
<label>Full Name</label>
<input type="text" id="name">
</div>

<div class="form-group">
<label>Email</label>
<input type="email" id="email">
</div>

<div class="form-group">
<label>Mobile Number</label>
<input type="text" id="mobile">
</div>

<div class="form-group">
<label>Gender</label>
<div class="gender">
<label><input type="radio" name="gender" value="Male"> Male</label>
<label><input type="radio" name="gender" value="Female"> Female</label>
</div>
</div>

<div class="form-group">
<label>Department</label>
<input type="text" id="department">
</div>

<div class="form-group">
<label>Course</label>
<select id="course">
<option value="">Select Course</option>
<option>Web Development</option>
<option>Artificial Intelligence</option>
<option>Data Science</option>
<option>Python Programming</option>
<option>Java Full Stack</option>
</select>
</div>

<div class="form-group">
<label>Skills</label>

<div class="skills">
<label><input type="checkbox" value="HTML"> HTML</label>
<label><input type="checkbox" value="CSS"> CSS</label>
<label><input type="checkbox" value="JavaScript"> JavaScript</label>
<label><input type="checkbox" value="Python"> Python</label>
</div>

</div>

<div class="form-group">
<label>Date of Birth</label>
<input type="date" id="dob">
</div>

<div class="form-group">
<label>Address</label>
<textarea id="address" rows="4"></textarea>
</div>

<button type="submit" class="submit">Submit</button>
<button type="reset" class="reset">Reset</button>

</form>

</div>

<div class="card">

<h2>Registered Students</h2>

<table>

<thead>
<tr>
<th>Name</th>
<th>Course</th>
<th>Department</th>
</tr>
</thead>

<tbody id="studentTable">
</tbody>

</table>

</div>

</div>

<footer>
<p>&copy; 2026 ABC Training Institute</p>
</footer>

<script>

document.getElementById("registrationForm").addEventListener("submit",function(event){

event.preventDefault();

let name=document.getElementById("name").value.trim();
let email=document.getElementById("email").value.trim();
let mobile=document.getElementById("mobile").value.trim();
let department=document.getElementById("department").value.trim();
let course=document.getElementById("course").value;
let dob=document.getElementById("dob").value;
let address=document.getElementById("address").value.trim();

let gender=document.querySelector('input[name="gender"]:checked');

let skills=[];

document.querySelectorAll('.skills input:checked').forEach(function(skill){
skills.push(skill.value);
});

if(name=="" || email=="" || mobile=="" || department=="" || course=="" || dob=="" || address=="" || !gender){
alert("Please fill all mandatory fields.");
return;
}

let emailPattern=/^[^ ]+@[^ ]+\.[a-z]{2,3}$/;

if(!emailPattern.test(email)){
alert("Invalid Email Address");
return;
}

let mobilePattern=/^[0-9]{10}$/;

if(!mobilePattern.test(mobile)){
alert("Mobile Number must contain exactly 10 digits");
return;
}

let birthDate=new Date(dob);
let today=new Date();

let age=today.getFullYear()-birthDate.getFullYear();

let month=today.getMonth()-birthDate.getMonth();

if(month<0 || (month===0 && today.getDate()<birthDate.getDate())){
age--;
}

if(age<=18){
alert("Age must be greater than 18");
return;
}

let table=document.getElementById("studentTable");

let row=table.insertRow();

row.insertCell(0).innerHTML=name;
row.insertCell(1).innerHTML=course;
row.insertCell(2).innerHTML=department;

document.getElementById("registrationForm").reset();

});

</script>

</body>
</html>
