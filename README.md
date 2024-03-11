<!DOCTYPE html>
<html>
<head>
    <title>To-Do List</title>
   <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
        }

        h1 {
            text-align: center;
            margin-top: 20px;
            color: #130c12;
        }

        #taskInput {
            width: 50%;
            padding: 10px;
            font-size: 16px;
        }

        #addButton, #clearButton {
            padding: 10px 20px;
            font-size: 16px;
            background-color: #313f06;
            color: #fff;
            border: none;
            cursor: pointer;
        }

        #addButton:hover, #clearButton:hover {
            background-color: #193705;
        }

        ul {
            list-style-type: none;
            padding: 0;
            margin: 20px auto;
            width: 70%;
        }

        li {
            background-color: #fff;
            margin: 10px 0;
            padding: 10px;
            border-radius: 5px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        button {
            padding: 5px 10px;
            font-size: 14px;
            background-color: #d9534f;
            color: #fff;
            border: none;
            border-radius: 3px;
            cursor: pointer;
        }

        button:hover {
            background-color: #c92cb1;
        }

        span {
            flex-grow: 1;
            margin-right: 10px;
        }
    </style>
</head>
<body>
    <h1>To-Do List</h1>
    
    <input type="text" id="taskInput" placeholder="please enter">
    <button id="addButton">Add list</button>
    <button id="clearButton">Clear All</button>
    
    <ul id="taskList">
    </ul>

    <script>
        const taskList = document.getElementById("taskList");
        const taskInput = document.getElementById("taskInput");
        const addButton = document.getElementById("addButton");
        const clearButton = document.getElementById("clearButton");

        addButton.addEventListener("click", addTask);
        clearButton.addEventListener("click", clearAll);

        function addTask() {
            const taskText = taskInput.value;

            if (taskText === "") {
                return;
            }

            const taskContainer = document.createElement("li");
            const taskItem = document.createElement("span");
            taskItem.textContent = taskText;

            const deleteButton = document.createElement("button");
            deleteButton.textContent = "Delete";
            deleteButton.addEventListener("click", function() {
                taskList.removeChild(taskContainer);
            });

            const updateButton = document.createElement("button");
            updateButton.textContent = "Update";
            updateButton.addEventListener("click", function() {
                updateTask(taskItem);
            });

            taskContainer.appendChild(taskItem);
            taskContainer.appendChild(updateButton);
            taskContainer.appendChild(deleteButton);

            taskList.appendChild(taskContainer);

            taskInput.value = "";
        }
        
        function updateTask(taskItem) {
            const updatedText = prompt("Enter the updated task:", taskItem.textContent);
            if (updatedText !== null) {
                taskItem.textContent = updatedText;
            }
        }

        function clearAll() {
            taskList.innerHTML = "";
        }
    </script>
</body>
</html>
