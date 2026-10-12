<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Моё местоположение</title>
</head>
<body>
  <h2>Определить местоположение</h2>

  <button onclick="getLocation()">Разрешить геолокацию</button>

  <p id="result"></p>

  <script>
    function getLocation() {
      if (!navigator.geolocation) {
        document.getElementById("result").textContent =
          "Геолокация не поддерживается.";
        return;
      }

      navigator.geolocation.getCurrentPosition(
        function(position) {
          const lat = position.coords.latitude;
          const lon = position.coords.longitude;

          document.getElementById("result").innerHTML =
            "Широта: " + lat + "<br>" +
            "Долгота: " + lon;
        },
        function() {
          document.getElementById("result").textContent =
            "Доступ к геолокации не разрешён.";
        }
      );
    }
  </script>
</body>
</html>
