<template lang="html">
  <div id="weatherApp" class="container-fluid">
  <header>
    <meta charset="utf-8">
    <meta http-equiv="x-ua-compatible" content="ie=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.8.1/css/all.css" integrity="sha384-50oBUHEmvpQ+1lW4y57PTFmhCaXp0ML5d60M1M7uH2+nqUivzIebhndOJK28anvf" crossorigin="anonymous">
  </header>
  
  <div class="container">
    <div class="row mb-4 justify-content-center">
  <h1 id="title" class="container-fluid my-3">Floyd myWeather</h1>
    </div>
  </div>

  <form class="form-inline lead justify-content-center" v-on:submit.prevent="citySearch(city)">
    <div class="input-group">
      <div class="input-group-prepend">
        <button type="submit" name="button" class="btn blue lead mb-4"><i class="fas fa-binoculars"></i></button>
      </div>
      <input v-model="city" id="z" type="text" class="lead search form-control" placeholder="Search by city" aria-label="Username" aria-describedby="basic-addon1">
      <div class="input-group-append">
        <button type="submit" name="button" class="btn blue lead mb-4"><i class="fas fa-binoculars"></i></button>
      </div>
    </div>
  </form>

<div v-if="Weather.length" class="">
  <div class="container">
    <div class="row mb-4 justify-content-center">
      <div class="btn-group flex-wrap">

        <div v-for="day in uniqueDaylist" class="mr-3 mb-3">
          <button  v-if="day[0]" type="button" class="btn btn-primary dropdown-toggle " data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
            {{day[0]}}
          </button>
          <div class="dropdown-menu">
            <div class="dropdown-divider"></div>
            <a v-on:click="construct(items.time, day[0])" v-for="items in Weather" v-bind:key="Weather.id" v-if="items.day == day[0]" class="dropdown-item" href="#">{{items.time}}</a>
          </div>
        </div>

        <div v-for="day in uniqueDaylist" class="mr-3 mb-3">
          <button v-if="day[1]" type="button" class="btn btn-primary dropdown-toggle " data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
            {{day[1]}}
          </button>
          <div class="dropdown-menu">
            <div class="dropdown-divider"></div>
            <a v-on:click="construct(items.time, day[1])" v-for="items in Weather" v-bind:key="Weather.id" v-if="items.day == day[1]" class="dropdown-item" href="#">{{items.time}}</a>
          </div>
        </div>

        <div v-for="day in uniqueDaylist" class="mr-3 mb-3">
          <button v-if="day[2]" type="button" class="btn btn-primary dropdown-toggle " data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
            {{day[2]}}
          </button>
          <div class="dropdown-menu">
            <div class="dropdown-divider"></div>
            <a v-on:click="construct(items.time, day[2])" v-for="items in Weather" v-bind:key="Weather.id" v-if="items.day == day[2]" class="dropdown-item" href="#">{{items.time}}</a>
          </div>
        </div>

        <div v-for="day in uniqueDaylist" class="mr-3 mb-3">
          <button v-if="day[3]" type="button" class="btn btn-primary dropdown-toggle " data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
            {{day[3]}}
          </button>
          <div class="dropdown-menu">
            <div class="dropdown-divider"></div>
            <a v-on:click="construct(items.time, day[3])" v-for="items in Weather" v-bind:key="Weather.id" v-if="items.day == day[3]" class="dropdown-item" href="#">{{items.time}}</a>
          </div>
        </div>

        <div v-for="day in uniqueDaylist" class="mr-3 mb-3">
          <button v-if="day[4]" type="button" class="btn btn-primary dropdown-toggle " data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
            {{day[4]}}
          </button>
          <div class="dropdown-menu">
            <div class="dropdown-divider"></div>
            <a v-on:click="construct(items.time, day[4])" v-for="items in Weather" v-bind:key="Weather.id" v-if="items.day == day[4]" class="dropdown-item" href="#">{{items.time}}</a>
          </div>
        </div>

        <div v-for="day in uniqueDaylist" class="mb-3">
          <button v-if="day[5]" type="button" class="btn btn-primary dropdown-toggle " data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
            {{day[5]}}
          </button>
          <div class="dropdown-menu">
            <div class="dropdown-divider"></div>
            <a v-on:click="construct(items.time, day[5])" v-for="items in Weather" v-bind:key="Weather.id" v-if="items.day == day[5]" class="dropdown-item" href="#">{{items.time}}</a>
          </div>

        </div>
      </div>
    </div>
  </div>

  <div id="fade" class="row mb-5 fade justify-content-center">
    <div class="col-11 col-lg-6 col-md-8 ">
      <ul class="list-group">
        <li class="list-group-item text-left grey" >
          <img id="logo" :src='this.Weather[0].icon' alt=""/><span class="mx-3" id="overcast">{{this.Weather[0].overcast}}</span>
          <a id="city" class="list-group-item list-group-item-action"  data-toggle="list"  role="tab" >{{this.Weather[0].city}}, at the current time.</a>
          <a id="time" class="list-group-item list-group-item-action"  data-toggle="list"  role="tab" >{{this.Weather[0].day}} {{this.Weather[0].date}} {{this.Weather[0].time}}</a>
          <a id="temp" class="list-group-item list-group-item-action"  data-toggle="list"  role="tab" >{{this.Weather[0].currentTemp}}</a>
          <a id="mintemp" class="list-group-item list-group-item-action"  data-toggle="list"  role="tab" >{{this.Weather[0].minTemp}}</a>
          <a id="maxtemp" class="list-group-item list-group-item-action"  data-toggle="list"  role="tab" >{{this.Weather[0].maxTemp}}</a>
          <a id="wind" class="list-group-item list-group-item-action"  data-toggle="list"  role="tab" >{{this.Weather[0].wind}}</a>
        </li>
      </ul>
    </div>
  </div>
  </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      Weather: [],
      Daylist: [],
      uniqueDaylist: [],
      myArray : {
        city: '',
        time: '',
        currentTemp: '',
        minTemp: '',
        maxTemp:'',
        wind: '',
        overcast: '',
        icon: '',
        day: '',
        daynight: '',
      },
    }
  },

  methods: {
    citySearch(city) {
      this.Weather=[];
      this.Daylist=[];
      this.uniqueDaylist=[];
      this.myArray={
        city: '',
        time: '',
        currentTemp: '',
        minTemp: '',
        maxTemp:'',
        wind: '',
        overcast: '',
        icon: '',
        day: '',
        daynight: '',
      }
      // CHECK IF INPUT IS EMPTY
      var input = document.getElementById('z').value;
      var whitecheck = /^\s*$/.test(city);
      if (input.length !== 0 && !whitecheck) {
      // MAKE INPUT HAVE ITS FIRST LETTER UPPERCASE AND THE REST LOWERCASE.
      var firstL = city.slice(0,1).toUpperCase(); //get the first character and make it Uppercase
      var rest = city.slice(1).toLowerCase(); //get the rest of the string and make it Lowercase
      var city = firstL.concat(rest); //create the new text store it

      // GET DATA FROM THE OPENWEATHERMAP API
      var weatherURI = 'http://api.openweathermap.org/data/2.5/forecast?q=' + city + '&units=metric&APPID=0b38ff1f9a3b7d41f3c382d42d099d03'
      this.axios.get(weatherURI).then((response) => {
        console.log(response.data)
        // FUNCTION TO TRANSFORM DATE DATA FROM API INTO ITS CORRESPONDING DAY OF THE WEEK.
        function getWeekDay(date){
        //Create an array containing each day, starting with Sunday.
        var weekdays = new Array(
         "Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"
        );
        //Use the getDay() method to get the day. The day is a number from 0 to 6.
        var day = date.getDay();
        //Return the element that corresponds to that index.
        return weekdays[day];
        }
        // CREATING OUR ARRAY OF DATA, FROM THE API'S JSON, FOR USAGE IN OUR APPLICATION.
        for (var i = 0; i<response.data.list.length; i++) {
        var date = new Date(response.data.list[i].dt_txt.slice(0,10));
        var weekDay = getWeekDay(date);
        this.Weather.push(this.myArray = {
        city: city,
        date: response.data.list[i].dt_txt.slice(0,10),
        time: response.data.list[i].dt_txt.slice(11,19),
        currentTemp: 'Average temperature is ' + response.data.list[i].main.temp + ' C°',
        minTemp: 'The lowest temperature possible is ' + response.data.list[i].main.temp_min + ' C°',
        maxTemp: 'The highest temperature possible is ' + response.data.list[i].main.temp_max + ' C°',
        wind: 'Wind speed is ' + response.data.list[i].wind.speed + ' m/s',
        overcast: response.data.list[i].weather[0].description,
        icon: "http://openweathermap.org/img/w/" + response.data.list[i].weather[0].icon + ".png",
        day: weekDay,
        daynight: response.data.list[i].weather[0].icon.slice(2,3),
      })
        }
        // CREATING AN ARRAY CONTAINING THE LIST OF DAYS.
        for (i = 0; i<response.data.list.length; i++) {
          switch(this.Weather[i].day) {
        case "Monday":this.Daylist.push('Monday');break;
        case "Tuesday":this.Daylist.push('Tuesday');break;
        case "Wednesday":this.Daylist.push('Wednesday');break;
        case "Thursday":this.Daylist.push('Thursday');break;
        case "Friday":this.Daylist.push('Friday');break;
        case "Saturday":this.Daylist.push('Saturday');break;
        case "Sunday":this.Daylist.push('Sunday');break;
      }
    }
      // REMOVE ANY DUPLICATES, FROM THE ARRAY OF DAYS, BY TRANSFORMTING IT INTO A SET.
      var unique = [...new Set(this.Daylist)];
      this.uniqueDaylist.push(unique)
          })
      } else {
        alert("Please input a valid city.");
      }
    },

    construct (time, day) {
      var elm = document.getElementById("fade");
      var newone = elm.cloneNode(true);
      elm.parentNode.replaceChild(newone, elm);
      function finder(weatherArray) {return weatherArray.day === day && weatherArray.time === time}
      document.getElementById("city").innerHTML = this.Weather[this.Weather.findIndex(finder)].city;
      document.getElementById("time").innerHTML = day + ' ' + this.Weather[this.Weather.findIndex(finder)].date + ' ' + time;
      document.getElementById("temp").innerHTML = this.Weather[this.Weather.findIndex(finder)].currentTemp;
      document.getElementById("mintemp").innerHTML = this.Weather[this.Weather.findIndex(finder)].minTemp;
      document.getElementById("maxtemp").innerHTML = this.Weather[this.Weather.findIndex(finder)].maxTemp;
      document.getElementById("wind").innerHTML = this.Weather[this.Weather.findIndex(finder)].wind;
      document.getElementById("overcast").innerHTML = this.Weather[this.Weather.findIndex(finder)].overcast;
      document.getElementById("logo").src = this.Weather[this.Weather.findIndex(finder)].icon;
      if (this.Weather[this.Weather.findIndex(finder)].daynight == 'd') {
        document.getElementById("city").innerHTML = this.Weather[this.Weather.findIndex(finder)].city + ' ,the sun is out <i class="fas fa-sun"></i>, it\'s daytime.';
        var body = document.getElementsByTagName('body')[0];
        body.className = " ";
        body.className = "day";
      } else {
        document.getElementById("city").innerHTML = this.Weather[this.Weather.findIndex(finder)].city + ' ,the moon is out <i class="fas fa-moon"></i>, it\'s night-time.';
        var body = document.getElementsByTagName('body')[0];
        body.className = " ";
        body.className = "night";
      }
    },

  }
}
</script>

<style lang="css">
a {
  cursor: pointer;
}

h1 {
  text-align: center;
  font-size: 2em;
}

body {
  background-color: black;
}

.lead {
  font-size: 1.2rem;
}

.blue {
  background-color: rgb(38, 99, 201);
  color: white;
}

.search {
  color: white;
  background-color: black;
  border: 1px rgb(38, 99, 201) solid;
}

.grey {
  background-color: rgb(134, 134, 134, 0.9);
  font-family: sans-serif;
}

#overcast {
  font-weight: bold;
  font-size: 18px;
}

button:hover {
  background-color: rgb(250, 5, 5, 0.8) !important;
  border: 1px solid white !important;
  color: white !important;
}

.day {
  background-color: #ff7a00;
  -webkit-transition: background-color 2s ease-out;
  -moz-transition: background-color 2s ease-out;
  -o-transition: background-color 2s ease-out;
  transition: background-color 2s ease-out;
}

.night {
  background-color: #420369;
  -webkit-transition: background-color 2s ease-out;
  -moz-transition: background-color 2s ease-out;
  -o-transition: background-color 2s ease-out;
  transition: background-color 2s ease-out;
}

.fade {
  -webkit-animation: fadein 2s; /* Safari, Chrome and Opera > 12.1 */
       -moz-animation: fadein 2s; /* Firefox < 16 */
        -ms-animation: fadein 2s; /* Internet Explorer */
         -o-animation: fadein 2s; /* Opera < 12.1 */
            animation: fadein 2s;
}

.fade:not(.show) {
    opacity: 1;
}

@keyframes fadein {
    from { opacity: 0; }
    to   { opacity: 1; }
}

/* Firefox < 16 */
@-moz-keyframes fadein {
    from { opacity: 0; }
    to   { opacity: 1; }
}

/* Safari, Chrome and Opera > 12.1 */
@-webkit-keyframes fadein {
    from { opacity: 0; }
    to   { opacity: 1; }
}

/* Internet Explorer */
@-ms-keyframes fadein {
    from { opacity: 0; }
    to   { opacity: 1; }
}

/* Opera < 12.1 */
@-o-keyframes fadein {
    from { opacity: 0; }
    to   { opacity: 1; }
}

#title {
      text-transform: uppercase;
      font-family: verdana;
      font-weight: 700;
      color: #f5f5f5;
      text-shadow: 1px 1px 1px orange,
          1px 2px 1px rgb(38, 99, 201),
          1px 3px 1px white,
          1px 4px 1px rgb(38, 99, 201),
          1px 5px 1px white,
          1px 6px 1px rgb(38, 99, 201),
          1px 7px 1px red,
          1px 8px 1px rgb(38, 99, 201),
          1px 9px 1px red,
          1px 10px 1px rgb(38, 99, 201),
      1px 18px 6px rgba(16,16,16,0.5),
      1px 22px 10px rgba(16,16,16,0.2),
      1px 25px 35px rgba(16,16,16,0.2),
      1px 30px 60px rgba(16,16,16,0.4);
}
</style>
