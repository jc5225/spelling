# spelling
<!DOCTYPE html>
<html>
<head>
	<title>Spelling Test</title>
	<script>
		function checkSpelling() {
			// Get the user's input
			var input = document.getElementById("input").value.toLowerCase();
			
			// Get the correct spelling of the word
			var word = document.getElementById("word").innerHTML.toLowerCase();
			
			// Compare the user's input to the correct spelling
			if (input === word) {
				document.getElementById("result").innerHTML = "Correct!";
			} else {
				document.getElementById("result").innerHTML = "Incorrect. The correct spelling is " + word + ".";
			}
			
			// Clear the input field
			document.getElementById("input").value = "";
			
			// Move on to the next word
			nextWord();
		}
		
		function nextWord() {
			// Get the next word from the list
			if (index < words.length - 1) {
				index++;
				document.getElementById("word").innerHTML = words[index];
			} else {
				document.getElementById("word").innerHTML = "End of test.";
			}
		}
		
		var words = [];
		var index = -1;
		
		function startTest() {
			// Get the list of words from the user
			words = document.getElementById("words").value.split(",");
			
			// Display the first word
			index = 0;
			document.getElementById("word").innerHTML = words[index];
			
			// Clear the result field
			document.getElementById("result").innerHTML = "";
			
			// Focus on the input field
			document.getElementById("input").focus();
		}
	</script>
</head>
<body>
	<h1>Spelling Test</h1>
	
	<label for="words">Enter a list of words:</label><br>
	<textarea id="words" rows="5" cols="50"></textarea><br><br>
	
	<button onclick="startTest()">Start Test</button><br><br>
	
	<label for="word">Spell the word:</label><br>
	<div id="word"></div><br>
	
	<label for="input">Type your answer:</label><br>
	<input type="text" id="input" onkeyup="if (event.keyCode === 13) checkSpelling()" autofocus><br>
	
	<div id="result"></div>
	
</body>
</html>
