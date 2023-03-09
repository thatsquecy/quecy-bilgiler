```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Chuck Norris Jokes</title>
</head>
<body>
  <h1>Chuck Norris Jokes</h1>
  <p id="joke"></p>

  <script>
    fetch('https://api.chucknorris.io/jokes/random')
      .then(response => response.json())
      .then(data => {
        const joke = data.value;
        document.getElementById('joke').textContent = joke;
      });
  </script>
</body>
</html>

```
```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Cat Pictures</title>
</head>
<body>
  <h1>Cat Pictures</h1>
  <img id="cat" src="" alt="Cat Picture">

  <script>
    fetch('https://api.thecatapi.com/v1/images/search')
      .then(response => response.json())
      .then(data => {
        const catUrl = data[0].url;
        document.getElementById('cat').src = catUrl;
      });
  </script>
</body>
</html>
```
```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Trivia Game</title>
</head>
<body>
  <h1>Trivia Game</h1>
  <p id="question"></p>
  <ul id="choices"></ul>

  <script>
    fetch('https://opentdb.com/api.php?amount=1&type=multiple')
      .then(response => response.json())
      .then(data => {
        const question = data.results[0].question;
        const choices = data.results[0].incorrect_answers.concat(data.results[0].correct_answer);

        document.getElementById('question').textContent = question;

        choices.forEach(choice => {
          const li = document.createElement('li');
          li.textContent = choice;
          document.getElementById('choices').appendChild(li);
        });
      });
  </script>
</body>
</html>
```
