<!--
Creator: Team editing by Cory
Market: SF
-->

![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)

# Making a Weather Directive

### Why is this important?
<!-- framing the "why" in big-picture/real world examples -->
*This workshop is important because:*

You'll get a chance to wrestle with creating a directive and adding behavior to a directive.

### What are the objectives?
<!-- specific/measurable goal for students to achieve -->
*After this workshop, developers will be able to:*

- Build a custom directive with a working controller.
- Make an `$http` call to an external API.

### Where should we be now?
<!-- call out the skills that are prerequisites -->
*Before this workshop, developers should already be able to:*

- Read third party API documentation and obtain an API key.
- Build a working Angular front end.
- Build a simple directive without any behavior

## Weather Widget

Today, you'll be building a current weather directive that will accept a string to specify the city and display the weather in that city. In the HTML, it will look like this:

```html
<current-weather city="San Francisco"></current-weather>
```
You'll be using the [Open Weather Map current weather API](http://openweathermap.org/api) and you'll need to get a key to use the API.

## How do I build this?

The dropdown below provides a basic order of steps to complete in order to build this directive. They don't need to be completed in this order exactly. **Please make an attempt at each of these steps before looking through the hints.**

<details>
  <summary>How do I go about building this?</summary><br>
  <ol>
    <li><details>
      <summary> Create a new repo and add your partner as a collaborator.</summary>
      <br>
      <ul>
        <li>Use GitHub to create a blank repo</li>
        ![image](https://cloud.githubusercontent.com/assets/6520345/18681178/c6847454-7f1b-11e6-9c9d-257ff8fe1c24.png)
        <li>Clone that repo to your computer, make a few empty files, and add a basic first commit.</li>
        <li>Go to the settings tab on the top left and then the collaborators section (select it on the right) and add your partner as a collaborator.</li>
        <li>The collaborator will get an email invite. Accept and then you too can clone the repo.</li>
      </ul>
    </details></li><br>
    <li><details>
      <summary> Set up a basic Angular front end</summary>
      <br><p>You made a gist about this! Go check it out! `app.js` should name the app, `index.html` should list all of the `<script>`s and `<link>`s to get your app wired up, and there should be a controller for the view we're working in.</p>
    </details></li><br>
    <li><details>
      <summary>Look at the API docs, get an API key, and make sure you can make a successful request to the [current weather API](http://openweathermap.org/api).</summary><br>
      <p>Just hit the subscribe button:</p>
      <img src="https://cloud.githubusercontent.com/assets/6520345/18678277/5e59bc6e-7f10-11e6-9070-c5f95b55c4ad.png">
      <br>
      <p>Get the free version:</p>
      <img src="https://cloud.githubusercontent.com/assets/6520345/18678305/78961ce4-7f10-11e6-9cf2-a0e19d97a7f2.png">
      <br><p>Make sure you know the url to hit and check out what the JSON results look like</p>
      <img src="https://cloud.githubusercontent.com/assets/6520345/18681431/e1c448d8-7f1c-11e6-95c0-27e3430dffd2.png">
    </details></li><br>
    <li><details>
      <summary>Build a working directive without any behavior. Make sure it accepts the city string.</summary>
      <br><p>Check out [yesterday's Cards Against Assembly card directive](https://github.com/sf-wdi-31/angular-custom-directives#know-the-code---independent) as a guide to build a simple directive.</p>
    </details></li><br>
    <li><details>
      <summary>Add a controller with the `$http` service as a dependency and make an `$http` call to the database</summary>
      <br>
      <p>

        ```javascript
        ...
          controllerAs: 'weatherCardCtrl',

          controller: weatherCardController,
        ...
        ```
        <br>
        <br>
        ```javascript
  weatherCardController.$inject = ['$http', '$scope'];
  function weatherCardController($http, $scope){
    var vm = this;
    var url="http://api.openweathermap.org/data/2.5/weather?mode=json&cnt=7&units=imperial&q=";
    var apikey = "&appid=" + '284c1c2d36e318ea0a389b743d94c747';
    vm.getWeather = function(city){
      console.log(url + city + apikey);
      $http({
        method: 'GET',
        url: url + city + apikey
      }).then(function(response){
          console.log(response);
          vm.weather = response.data;
        }, function(err){
          console.log(err);
        });
    };
    vm.getWeather($scope.city);
  };
  ```
      </p>
    </details></li><br>
    <li><details>
      <summary>Make the template reflect the data that you want!</summary>
      <br>
      <p>
        A very simple template could look like this:
        ```html
          <div class="current-weather">
            <h4>Weather for {{city}}</h4>
            {{weather.main.temp}}
          </div>
        ```
      </p>
    </details></li><br>
    <li><details>
      <summary>Tie all of the pieces together and add some styling</summary>
      <br>
      <p>
        [Here is the full solution  ](https://github.com/sf-wdi-31/weather-directive) with a few notes about the details.
      </p>
    </details></li>
  </ol>

</details>
