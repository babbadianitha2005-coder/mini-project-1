<!DOCTYPE html>
<html>
<head>
    <title>Interactive Survey Form Builder</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            background: #f4f4f4;
        }

        .container {
            max-width: 800px;
            margin: auto;
        }

        .box {
            background: white;
            padding: 20px;
            margin-bottom: 20px;
            border-radius: 10px;
        }

        input[type="text"] {
            width: 70%;
            padding: 10px;
            margin-right: 10px;
        }

        button {
            padding: 10px 15px;
            cursor: pointer;
        }

        .question {
            margin: 10px 0;
        }

        h2 {
            color: #333;
        }
    </style>
</head>
<body>

<div class="container">

    <div class="box">
        <h2>Survey Builder</h2>

        <input type="text" id="questionInput"
               placeholder="Enter survey question">
        <button onclick="addQuestion()">Add Question</button>

        <h3>Questions Added:</h3>
        <ul id="questionList"></ul>

        <button onclick="generateSurvey()">Generate Survey</button>
    </div>

    <div class="box">
        <h2>Survey Preview</h2>
        <form id="surveyForm"></form>
    </div>

</div>

<script>
    let questions = [];

    function addQuestion() {
        const input = document.getElementById("questionInput");
        const question = input.value.trim();

        if(question === "") {
            alert("Please enter a question.");
            return;
        }

        questions.push(question);

        const li = document.createElement("li");
        li.textContent = question;
        document.getElementById("questionList").appendChild(li);

        input.value = "";
    }

    function generateSurvey() {
        const surveyForm = document.getElementById("surveyForm");
        surveyForm.innerHTML = "";

        questions.forEach((question, index) => {
            const div = document.createElement("div");
            div.className = "question";

            div.innerHTML = `
                <label><b>${question}</b></label><br>
                <input type="text" placeholder="Your answer"><br><br>
            `;

            surveyForm.appendChild(div);
        });

        if(questions.length > 0) {
            const submitBtn = document.createElement("button");
            submitBtn.type = "submit";
            submitBtn.textContent = "Submit Survey";
            surveyForm.appendChild(submitBtn);
        }
    }
</script>

</body>
</html>
