<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title>Math Addition Test</title>
	<style>
		body {
			background-color: #f2f2f2;
			font-family: Arial, sans-serif;
			color: #333;
			text-align: center;
		}
		h1 {
			margin-top: 50px;
			font-size: 36px;
			font-weight: bold;
			text-transform: uppercase;
			letter-spacing: 2px;
		}
		form {
			margin-top: 30px;
			display: flex;
			flex-direction: column;
			align-items: center;
		}
		label {
			font-size: 24px;
			margin-bottom: 10px;
		}
		input[type="number"] {
			font-size: 24px;
			padding: 10px;
			border-radius: 5px;
			border: none;
			box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.3);
		}
		button.check {
			background-color: #4CAF50;
			color: white;
			font-size: 24px;
			padding: 10px;
			border-radius: 5px;
			border: none;
			box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.3);
			margin-top: 20px;
			width: 200px;
			height: 60px;
		}
		button.next {
			background-color: #008CBA;
			color: white;
			font-size: 24px;
			padding: 10px;
			border-radius: 5px;
			border: none;
			box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.3);
			margin-top: 20px;
			width: 200px;
			height: 60px;
		}
		button.container {
			display: flex;
			justify-content: center;
			align-items: center;
			width: 100%;
			height: 60px;
		}
		.answer {
			font-size: 24px;
			margin-top: 20px;
		}
        #feedback {
  font-size: 28px;
  margin-top: 20px;
}
	</style>
</head>

<body>
	<h1>Math Addition Test</h1>
	<form>
		<label>What is <span id="num1"></span> + <span id="num2"></span>?</label>
		<input type="number" id="result" required>
		<div class="container">
			<button class="check" type="button" onclick="checkAnswer()">Check Answer</button>
			<button class="next" type="button" onclick="nextQuestion()">Next Question</button>
		</div>
		<div id="feedback"></div>
		<div class="result" id="correct"></div>
	</form>
	<script>
		var num1, num2, correctAnswer;

		function generateQuestion() {
			num1 = Math.floor(Math.random() * 100);
			num2 = Math.floor(Math.random() * 100);
			correctAnswer = num1 + num2;
			document.getElementById("num1").innerHTML = num1;
			document.getElementById("num2").innerHTML = num2;
			document.getElementById("result").value = "";
			document.getElementById("feedback").innerHTML = "";

			document.getElementById("correctAnswer").innerHTML = "";
		}

		function checkAnswer() {
			answer = document.getElementById("result").value;
			if (answer == correctAnswer) {
				document.getElementById("feedback").innerHTML = "Correct!";
				document.getElementById("correct").innerHTML = "";
			} else {
				document.getElementById("feedback").innerHTML = "Incorrect.";
				document.getElementById("correct").innerHTML = "The correct answer is " + correctAnswer + ".";
			}
		}

		function nextQuestion() {
			generateQuestion();
		}

		generateQuestion();
	</script>
</body>
</html>
