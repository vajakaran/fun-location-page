# fun-location-page
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Fun Surprise!</title>
  <style>
    body {
      font-family: 'Comic Sans MS', cursive, sans-serif;
      background: linear-gradient(to right, #ffecd2 0%, #fcb69f 100%);
      text-align: center;
      padding: 50px;
    }
    .box {
      background: white;
      padding: 30px;
      border-radius: 15px;
      box-shadow: 0 0 20px rgba(0,0,0,0.2);
      display: inline-block;
    }
    button {
      padding: 15px 25px;
      font-size: 18px;
      border: none;
      border-radius: 10px;
      background: #ff6f61;
      color: white;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <div class="box">
    <h2>Hey Bestie!</h2>
    <p>Let's play a quick fun game! Just click below to share your location.</p>
    <button onclick="getLocation()">Share My Location</button>
    <p id="status"></p>
  </div>

  <script>
    function getLocation() {
      const status = document.getElementById('status');
      if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(showPosition, showError);
        status.innerText = "Fetching your location...";
      } else {
        status.innerText = "Geolocation is not supported by this browser.";
      }
    }

    function showPosition(position) {
      const lat = position.coords.latitude;
      const lon = position.coords.longitude;
      const link = `https://www.google.com/maps?q=${lat},${lon}`;
      document.getElementById('status').innerHTML = `Thanks! Here's your location: <br><a href="${link}" target="_blank">${link}</a>`;
      // Aap yahan backend pe data bhejne ka system laga sakte ho agar chaho
    }

    function showError(error) {
      document.getElementById('status').innerText = "Location access denied or failed.";
    }
  </script>
</body>
</html>
