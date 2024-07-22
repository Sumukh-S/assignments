d. Display calendar for the month and year selected from combo box
index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Display Calendar</title>
    <script src="displayCalendar.js"></script>
</head>
<body>
    <label for="month">Month:</label>
    <select id="month" onchange="displayCalendar()">
        <option value="0">January</option>
        <option value="1">February</option>
        <option value="2">March</option>
        <option value="3">April</option>
        <option value="4">May</option>
        <option value="5">June</option>
        <option value="6">July</option>
        <option value="7">August</option>
        <option value="8">September</option>
        <option value="9">October</option>
        <option value="10">November</option>
        <option value="11">December</option>
    </select>
    
    <label for="year">Year:</label>
    <input type="number" id="year" value="2023" onchange="displayCalendar()">
    
    <div id="calendar"></div>
</body>
</html>
displayCalendar.js
function displayCalendar() {
    var month = document.getElementById("month").value;
    var year = document.getElementById("year").value;
    var firstDay = new Date(year, month, 1).getDay();
    var daysInMonth = new Date(year, parseInt(month) + 1, 0).getDate();
    var calendar = "<table><tr><th>Sun</th><th>Mon</th><th>Tue</th><th>Wed</th><th>Thu</th><th>Fri</th><th>Sat</th></tr><tr>";

    for (var i = 0; i < firstDay; i++) {
        calendar += "<td></td>";
    }
    for (var day = 1; day <= daysInMonth; day++) {
        calendar += "<td>" + day + "</td>";
        if ((firstDay + day) % 7 == 0) {
            calendar += "</tr><tr>";
        }
    }
    calendar += "</tr></table>";

    document.getElementById("calendar").innerHTML = calendar;
}

e. On mouse over event
index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mouse Over Event</title>
    <script src="mouseOverEvent.js"></script>
    <style>
        .hover-box {
            width: 200px;
            height: 100px;
            border: 1px solid black;
            text-align: center;
            line-height: 100px;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div class="hover-box" onmouseover="mouseOver()" onmouseout="mouseOut()">Hover over me!</div>
    <div id="message"></div>
</body>
</html>
mouseOverEvent.js
function mouseOver() {
    document.getElementById("message").innerText = "Mouse is over the box!";
}

function mouseOut() {
    document.getElementById("message").innerText = "";
}
