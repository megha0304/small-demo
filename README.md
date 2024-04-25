# small-demo


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Location Checker</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
    }
    #location {
      font-size: 24px;
      margin-top: 20px;
    }
  </style>
</head>
<body>
  <h1>Location Checker</h1>
  <button onclick="getLocation()">Get Location</button>
  <p id="location"></p>

  <script>
    function getLocation() {
      if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(showPosition, showError);
      } else {
        document.getElementById("location").innerHTML = "Geolocation is not supported by this browser.";
      }
    }

    function showPosition(position) {
      var latitude = position.coords.latitude;
      var longitude = position.coords.longitude;
      document.getElementById("location").innerHTML = "Latitude: " + latitude + "<br>Longitude: " + longitude;
    }

    function showError(error) {
      switch(error.code) {
        case error.PERMISSION_DENIED:
          document.getElementById("location").innerHTML = "User denied the request for Geolocation.";
          break;
        case error.POSITION_UNAVAILABLE:
          document.getElementById("location").innerHTML = "Location information is unavailable.";
          break;
        case error.TIMEOUT:
          document.getElementById("location").innerHTML = "The request to get user location timed out.";
          break;
        case error.UNKNOWN_ERROR:
          document.getElementById("location").innerHTML = "An unknown error occurred.";
          break;
      }
    }
  </script>
</body>
</html>
