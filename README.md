# Daily Schedule 

Create a simple calendar application that allows a user to save events for each hour of the day. This app will run in the browser and feature dynamically updated HTML and CSS 

## Screenshot
![SCREEN SHOT URL](https://i.imgur.com/7PQgHBT.png)

## Code

GIVEN I am using a daily planner to create a schedule
WHEN I open the planner
THEN the current day is displayed at the top of the calendar

```Javascript
    const date = moment(new Date());
    
    function displayDate() {
      const currentDayString = date.format('dddd') + ', ' + date.format('MMMM') + " " + moment().date();
      document.getElementById('currentDay').innerHTML = currentDayString;
    }
```

WHEN I scroll down
THEN I am presented with time blocks for standard business hours

```HTML
displayDate();

    const container = document.getElementById('container');

    for (let i=1; i<25; i++) {
      const timeBlock = document.createElement('div');
      timeBlock.className = 'time-block';
      container.append(timeBlock);

      const hourDiv = document.createElement('div');
      hourDiv.className = 'hour-div';
      if (i >12) {
        resetTime = i -12;
        hourDiv.innerHTML = resetTime + "PM";
      } else {
        hourDiv.innerHTML = i + "AM";
      }
      timeBlock.append(hourDiv);

      const eventDiv = document.createElement('textarea');
      eventDiv.className = 'event-div';

      if (localStorage.getItem(hourDiv.innerText)) {

      }
```

WHEN I view the time blocks for that day
THEN each time block is color-coded to indicate whether it is in the past, present, or future

```CSS
.past-event {
  background-color: grey;
}
.current-event {
  background-color: red;
}

.future-event{
  background-color:green;
}
```

WHEN I click into a time block
THEN I can enter an event

```
const eventDiv = document.createElement('textarea');
```
WHEN I click the save button for that time block
THEN the text for that event is saved in local storage

```
      saveButton.onclick = function() {
         localStorage.setItem(hourDiv.innerText, eventDiv.value);
      }
```
WHEN I refresh the page
THEN the saved events persist

```
      eventDiv.innerHTML = localStorage.getItem(hourDiv.innerText) || "";
  
```

## Contributing
Pull requests are welcome. 