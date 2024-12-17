# CRUD-Operation

Name: SAHINA BARVEEN.S
Company:CORIZO
ID:WIPRO ID-CRZ77985
Domain:Full Stack Web Development
Duration:November2024 to January 2025
Mentor:Saravanan

Overview of the Project

Introduction to CRUD Operations Using HTML, CSS, and JavaScript
CRUD stands for Create, Read, Update, and Delete — the four basic operations used in managing data within an application. These operations are fundamental in building any database-driven system, where users can add, view, modify, and remove data. Implementing CRUD operations in a front-end web application provides a hands-on approach to understanding how data can be manipulated using client-side technologies.

In this project, we will explore how to implement CRUD operations using HTML, CSS, and JavaScript. These technologies, while not typically used to manage back-end databases directly, can be used to create interactive, dynamic interfaces where users can perform CRUD-like actions locally on the browser.

1. Create Operation
The Create operation involves adding new data. In our web application, a user can fill out a form with input fields, such as a name or email address, and submit the form to create a new record. The JavaScript function handles this by adding the new data to an array, and dynamically updating the user interface (UI) to display the new record.
2. Read Operation
The Read operation refers to the action of displaying or viewing the data. When a user enters data, it’s stored in an array or a temporary data structure. The app then reads this data and displays it in a table format, allowing users to see the list of records they have created. This can be achieved by dynamically updating the HTML with JavaScript.
3. Update Operation
The Update operation allows users to modify existing data. In the CRUD application, a user can click an "Edit" button next to an entry, which pre-populates the form with the selected data. After the user makes changes and submits the form again, JavaScript updates the relevant record in the array and the UI is updated to reflect the changes.
4. Delete Operation
The Delete operation allows users to remove data. A "Delete" button next to each entry lets users delete specific records from the list. Upon clicking, JavaScript removes the selected record from the array and updates the table to show the remaining entries.

How Does It Work?
HTML forms and tables are used to capture and display data.
CSS ensures the layout is clean, organized, and interactive.
JavaScript manages the logic for adding, editing, and deleting data by manipulating the Document Object Model (DOM), which dynamically updates the web page in response to user actions.

1. Variables and Selectors
 let data = [];
let editId = null;
•	data: An array to store the records (objects with id, name, and age).
•	editId: A variable to track the id of the record being edited. If editId is null, the form creates a new record.
const form = document.getElementById('crud-form');
const nameInput = document.getElementById('name');
const ageInput = document.getElementById('age');
const tableBody = document.getElementById('table-body');
const submitBtn = document.getElementById('submit-btn');

These const variables store references to elements in the HTML using their IDs:
•	form: The form element where users enter name and age.
•	nameInput and ageInput: Input fields for entering the name and age.
•	tableBody: The <tbody> in the HTML table where records are displayed.
•	submitBtn: The button in the form used to add or update a record.

2. Form Submission
form.addEventListener('submit', function (e) {
  e.preventDefault();
•	Purpose: Listen for the submit event on the form.
•	e.preventDefault(): Prevents the default behavior of form submission, which reloads the page.
3. Add or Update Record
 
const name = nameInput.value.trim();
const age = ageInput.value.trim();
•	Get Input Values: The entered name and age values are trimmed (extra spaces removed).
 
if (editId) {
  // Update Record
  const record = data.find((item) => item.id === editId);
  record.name = name;
  record.age = age;
  editId = null;
  submitBtn.textContent = "Add Record";
} else {
  // Create Record
  const newRecord = {
    id: Date.now(),
    name,
    age,
  };
  data.push(newRecord);
}
Check if Editing: If editId is set:
•	Find the record in data using its id.
•	Update its name and age values.
•	Reset editId to null and change the button text to "Add Record".
Create a New Record: If editId is null:
•	Create a new record with a unique id (using Date.now()), name, and age.
•	Add the record to the data array.
4. Render the Table
 function renderTable() {
  tableBody.innerHTML = '';
  data.forEach((item) => {
    const row = document.createElement('tr');

    row.innerHTML = `
      <td>${item.id}</td>
      <td>${item.name}</td>
      <td>${item.age}</td>
      <td>
        <button class="action-btn edit-btn" onclick="editRecord(${item.id})">Edit</button>
        <button class="action-btn delete-btn" onclick="deleteRecord(${item.id})">Delete</button>
      </td>
    `;

    tableBody.appendChild(row);
  });
}
•	Purpose: Clears the table and dynamically re-creates it from the data array.
•	For each record in data, a new table row (<tr>) is created with:
•	The record's id, name, and age.
•	Buttons for Edit and Delete, each linked to their respective functions using the record's id.
5. Edit Record
function editRecord(id) {
  const record = data.find((item) => item.id === id);
  nameInput.value = record.name;
  ageInput.value = record.age;
  editId = id;
  submitBtn.textContent = "Update Record";
}
•	Purpose: Allows a user to edit an existing record.
•	Find the record in data using its id.
•	Populate the form fields (nameInput and ageInput) with the record's values.
•	Set editId to the record's id and change the button text to "Update Record".
6. Delete Record
function deleteRecord(id) {
  data = data.filter((item) => item.id !== id);
  renderTable();
}
•	Purpose: Deletes a record by its id.
•	Filter out the record with the specified id from the data array.
•	Re-render the table to reflect the changes.


7. Initial Render
 renderTable();
•	Ensures the table is rendered when the page is first loaded.
How the Code Works in a Flow
The user enters a name and age in the form and submits it.
If adding:
A new record is created with a unique id and added to data.
If editing:
The existing record in data is updated.
After submission:
The renderTable function is called to display the updated records.
Users can edit or delete records using the buttons in the table.

![Screenshot 2024-12-18 083059](https://github.com/user-attachments/assets/235747c8-1f9b-4700-835c-0c3aa4c95aa1)
![Screenshot 2024-12-18 083254](https://github.com/user-attachments/assets/24daadb4-33d4-4119-a542-4d91b7fe921d)

