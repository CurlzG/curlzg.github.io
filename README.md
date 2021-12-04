# curlz.github.io
<!DOCTYPE html>
<html>
    <head>
        <title>Save Our Paws</title>
      </head>
<style>
  @import url(https://fonts.googleapis.com/css?family=Roboto:400,900);

.module {
  background: 
    linear-gradient(
      rgba(0, 0, 0, 0.6),
      rgba(0, 0, 0, 0.6)
    ),
    url(https://s3-us-west-2.amazonaws.com/s.cdpn.io/3/skyscrapers.jpg);
  background-size: cover;
  width: 300px;
  height: 200px;
  margin: 10px 0 0 10px;
  position: relative;
  float: left;
}
.module1 {
    background: 
      linear-gradient(
        rgba(0, 0, 0, 0.6),
        rgba(0, 0, 0, 0.6)
      ),
      url(grass.jpg);
    background-size: cover;
    width: 300px;
    height: 200px;
    margin: 10px 0 0 10px;
    position: relative;
    float: left;
  }
  .module2 {
    background: 
      linear-gradient(
        rgba(0, 0, 0, 0.6),
        rgba(0, 0, 0, 0.6)
      ),
      url(dirt.jpeg);
    background-size: cover;
    width: 300px;
    height: 200px;
    margin: 10px 0 0 10px;
    position: relative;
    float: left;
  }
  .module3 {
    background: 
      linear-gradient(
        rgba(0, 0, 0, 0.6),
        rgba(0, 0, 0, 0.6)
      ),
      url(concrete.jpg);
    background-size: cover;
    width: 300px;
    height: 200px;
    margin: 10px 0 0 10px;
    position: relative;
    float: left;
  }
  .module4 {
    background: 
      linear-gradient(
        rgba(0, 0, 0, 0.6),
        rgba(0, 0, 0, 0.6)
      ),
      url(tarmac.jpg);
    background-size: cover;
    width: 300px;
    height: 200px;
    margin: 10px 0 0 10px;
    position: relative;
    float: left;
  }

.top h2 {
  color: white;
  margin: 0;
  padding: 20px;
}

.lr p {
  font-family: 'Roboto', sans-serif;
  position: absolute;
  bottom: 20px;
  left: 20px;
  color: white;
  margin: 0;
}

.mid h2 {
  font-family: 'Roboto', sans-serif;
  font-weight: 900;
  color: white;
  text-transform: uppercase;
  margin: 0;
  position: absolute;
  top: 20%;
  left: 50%;
  font-size: 2rem;
  transform: translate(-50%, -50%);
}
.mid h4 {
    font-family: 'Roboto', sans-serif;
    font-weight: 900;
    color: white;
    text-transform: uppercase;
    margin: 0;
    position: absolute;
    top: 40%;
    left: 50%;
    font-size: 1.5rem;
    transform: translate(-50%, -50%);
  }
  .mid h5 {
    font-family: 'Roboto', sans-serif;
    font-weight: 900;
    color: white;
    text-transform: uppercase;
    margin: 0;
    position: absolute;
    top: 40%;
    left: 50%;
    font-size: 1.5rem;
    transform: translate(-50%, -50%);
  }

.cap p {
  padding: 20px;
  color: white;
  font: 12px Monaco, Mono-Space;
  margin: 0;
}
  </style> 
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link rel="stylesheet" href="mystyle.css">
<body>

<div> 
    

  
  <div class="module4 mid">
    <h2>Tarmac</h2>
    <h4 id="Tarmac"></h4>
  </div>
  <div class="module3 mid">
    <h2>Concrete</h2>
    <h4 id="concrete"></h4>
  </div>
  
  <br style="clear: both;">
  <div class="module2 mid">
    <h2>Dirt</h2>
    <h4 id="dirt"> </h4>
  </div>
  <div class="module1 mid">
    <h2>Grass</h2>
    <h4 id="grass"></h4>
  </div>
  <br style="clear: both;">
  <br style="clear: both;">

  
    </div>
    <form action="/action_page.php">
        <label for="fname">Tarmac:</label>
        <input type="text" id="fname" name="fname"><br><br>
        <label for="lname">Concrete:</label>
        <input type="text" id="lname" name="lname"><br><br>
        <label for="lname">Dirt:</label>
        <input type="text" id="lname" name="dirt"><br><br>
        <label for="lname">Grass:</label>
        <input type="text" id="lname" name="grass"><br><br>
        <input type="submit" value="Submit">
      </form>
      <div> 
          <p id="text"> </p>
      </div>
    <script>

  if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition(getSafety);
  } else { 
    x.innerHTML = "Geolocation is not supported by this browser.";
  }

function showPosition(position) {
  x.innerHTML = "Latitude: " + position.coords.latitude + 
  "<br>Longitude: " + position.coords.longitude;
}

function getSafety(position) {
        const url = "http://api.openweathermap.org/data/2.5/weather?lat=" + position.coords.latitude +"&lon=" + position.coords.longitude + "&appid=6a2161db551567da1d5e7be49c9b7596&units=metric";
  fetch(url).then(data => {
    return data.json();
  }).then(function(data){
    document.getElementById("text").innerHTML = JSON.stringify(data)
    let value = 0;
    const temp = data.main.temp; 
    const wind = data.wind.speed;
    const cloud = data.clouds.all;
    if(temp*2 <= 42){
        document.getElementById("Tarmac").innerHTML = "Safe"
        document.getElementById("concrete").innerHTML = "Safe"
        document.getElementById("dirt").innerHTML = "Safe"
        document.getElementById("grass").innerHTML = "Safe"
    } else {
      if(wind <= 5 && cloud <= 5 ){
        value = value+(temp*2);
      }
      if (value >= 49 && value <= 60){
        document.getElementById("Tarmac").innerHTML = "Not Safe"
        document.getElementById("concrete").innerHTML = "Not Safe"
        document.getElementById("dirt").innerHTML = "Safe"
        document.getElementById("grass").innerHTML = "Safe"
      }
      if(value >= 65){

        document.getElementById("Tarmac").innerHTML = "Danger"
        document.getElementById("concrete").innerHTML = "Danger"
        document.getElementById("dirt").innerHTML = "Danger"
        document.getElementById("grass").innerHTML = "Danger"
      }
    }
  });  
}
    </script>


</body>
</html>
