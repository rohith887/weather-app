# weather-app
 From this we can know  about the weather in any location with the aid of our JavaScript weather app. Any city’s information, including the temperature, date, and sky conditions, can be found below if you enter its name in the input box below.

The weather in any city in the world can be simply known with the use of this straightforward weather application. With the aid of JQuery, this design is simple to create. The creation of this application in pure JavaScript is simple, though, if you choose.

You certainly need to understand JavaScript at a basic level. It’s fairly simple to do if you have a basic understanding of JS. Since this is intended for beginners, I’ve provided a thorough, step-by-step explanation of why I chose to utilize that particular code line.

The weather information for all towns and nations was fetched using the APIs in our weather app. I’m not sure how many of you are familiar with APIs, but if you’re not, don’t worry; we designed this project beginner-friendly, so we will explain every concepts that we used in our project.

### HTML CODE
```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Quiz App</title>
    <link rel="stylesheet" href="style.css" />
</head>

<body>

    <script src="index.js"></script>
</body>
<header>
   <input type="text" autocomplete="off" class="search-box" placeholder="Search for a city">
<main>
            <section class="location">
                <div class="city">Hyderabad,Telangana </div>
                <div class="date">Wednesday 14 September</div>
            </section>
            <div class="current">
               <div class="temp">15<span>°C</span></div>
               <div class="weather">Sunny</div>
               <div class="hi-low">13°C / 16°C</div>
           </div>
       </main>
</header>
</html>
```
### CSS CODE
```
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  font-family: "Outfit", sans-serif;
  background-image: url("    https://images3.alphacoders.com/109/1091500.jpg");
  background-size: cover;
  background-position: top center;
}
.app-wrap {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  background-image: linear-gradient(
    to bottom,
    rgba(0, 0, 0, 0.3),
    rgba(0, 0, 0, 0.6)
  );
}
header {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 50px 15px 15px;
}
header input {
  width: 100%;
  max-width: 280px;
  padding: 10px 15px;
  border: none;
  outline: none;
  background-color: rgba(18, 18, 18, 0.4);
  border-radius: 16px;
  border-bottom: 3px solid #df8e00;

  font-size: 20px;
  font-weight: 300;
  transition: 0.2s ease-out;
  color: #eeeeee;
}
header input:focus {
  background-color: rgba(18, 18, 18, 0.8);
}
main {
  flex: 1 1 100%;
  padding: 25px 25px 50px;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}
.location .city {
  color: #eeeeee;
  font-size: 32px;
  font-weight: 500;
  margin-bottom: 5px;
}
.location .date {
  color: #eeeeee;
  font-size: 16px;
}
.current .temp {
  color: #eeeeee;
  font-size: 102px;
  font-weight: 900;
  margin: 30px 0;
  text-shadow: 2px 8px rgba(0, 0, 0, 0.5);
}
.current .temp span {
  font-weight: 200;
}
.current .weather {
  color: #eeeeee;
  font-size: 32px;
  font-weight: 700;
  font-style: italic;
  margin-bottom: 15px;
  text-shadow: 0 3px rgba(0, 0, 0, 0.4);
}
.current .hi-low {
  color: #eeeeee;
  font-size: 24px;
  font-weight: 500;
  text-shadow: 0 3px rgba(0, 0, 0, 0.4);
}
```

Let’s look at the finished result now that we have finished styling
![Screenshot (133)](https://github.com/rohith887/weather-app/assets/94122677/484432d9-e306-40ae-9c79-5d3baa056933)

### JAVA SCRIPT CODE
```
const api = {
  key: "2fa73590fd8b5a4c6e68098ad5625395",
  base: "https://api.openweathermap.org/data/2.5/"
};

const searchbox = document.querySelector(".search-box");
searchbox.addEventListener("keypress", setQuery);

function setQuery(evt) {
  if (evt.keyCode == 13) {
    getResults(searchbox.value);
  }
}

function getResults(query) {
  fetch(`${api.base}weather?q=${query}&units=metric&APPID=${api.key}`)
    .then((weather) => {
      return weather.json();
    })
    .then(displayResults);
}

function displayResults(weather) {
  console.log(weather);
  let city = document.querySelector(".location .city");
  city.innerText = `${weather.name}, ${weather.sys.country}`;

  let now = new Date();
  let date = document.querySelector(".location .date");
  date.innerText = dateBuilder(now);

  let temp = document.querySelector(".current .temp");
  temp.innerHTML = `${Math.round(weather.main.temp)}<span>°C</span>`;

  let weather_el = document.querySelector(".current .weather");
  weather_el.innerText = weather.weather[0].main;

  let hilow = document.querySelector(".hi-low");
  hilow.innerText = `${weather.main.temp_min}°C / ${weather.main.temp_max}°C`;
}

function dateBuilder(d) {
  let months = [
    "January",
    "February",
    "March",
    "April",
    "May",
    "June",
    "July",
    "August",
    "September",
    "October",
    "November",
    "December"
  ];
  let days = [
    "Sunday",
    "Monday",
    "Tuesday",
    "Wednesday",
    "Thursday",
    "Friday",
    "Saturday"
  ];

  let day = days[d.getDay()];
  let date = d.getDate();
  let month = months[d.getMonth()];
  let year = d.getFullYear();

  return `${day} ${date} ${month} ${year}`;
}
```


