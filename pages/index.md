<!DOCTYPE html>
<html>
<head>
	<title>Data Entry Form</title>
</head>
<body>
	<h1>Data Entry Form</h1>
	<form method="POST" action="save_data.php">
		<label for="hazard">Hazard:</label>
		<input type="text" id="hazard" name="hazard"><br><br>
		<label for="type">Type:</label>
		<select id="type" name="type">
			<option value="apples">Apples</option>
			<option value="pears">Pears</option>
			<option value="oranges">Oranges</option>
		</select><br><br>
		<label for="value">Value:</label>
		<input type="text" id="value" name="value"><br><br>
		<input type="submit" value="Submit">
	</form>
	<div id="message"></div>
	<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
	<script>
		$(document).ready(function() {
			$('form').submit(function(event) {
				event.preventDefault();
				var formData = {
					'hazard': $('input[name=hazard]').val(),
					'type': $('select[name=type]').val(),
					'value': $('input[name=value]').val()
				};
				$.ajax({
					type: 'POST',
					url: 'save_data.php',
					data: formData,
					dataType: 'json',
					encode: true
				}).done(function(data) {
					$('#message').html('Thank you for submitting your data.');
				});
			});
		});
	</script>
</body>
</html>
