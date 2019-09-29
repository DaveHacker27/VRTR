# VRTR
Trash roboter
<!DOCTYPE html>
<html>
<head>
<title>
VRTR-STEUERUNG
</title>
<style>
button{
	height: 100px;
	width: 100px;
	background-color: red;
}
</style>
<script>
var rpi = "http://151.216.2.49:5000";
function forward() {
var status=document.querySelector("#status_text");
status.innerHTML="Fahre vorwärts!";
fetch(rpi+"/api/forward");
}
function stop() {
var status=document.querySelector("#status_text");
status.innerHTML="Stop!";
fetch(rpi+"/api/stop");
}
function backward() {
var status=document.querySelector("#status_text");
status.innerHTML="Fahre rückwärts!";
fetch(rpi+"/api/backward");
}
function right() {
var status=document.querySelector("#status_text");
status.innerHTML="Fahre nach rechts!";
fetch(rpi+"/api/right");
}
function left() {
var status=document.querySelector("#status_text");
status.innerHTML="Fahre nach links!";
fetch(rpi+"/api/left");
}

document.addEventListener("keydown",event=>{
	switch(event.keyCode) {
		case 87:
		forward();
		break;
		case 65:
		left();
		break;
		case 83:
		backward();
		break;
		case 68:
		right();
		break;
	}
console.log(event);
});
document.addEventListener("keyup",event=>{
	switch(event.keyCode) {
		case 87:
		stop();
		break;
		case 65:
		stop();
		break;
		case 83:
		stop();
		break;
		case 68:
		stop();
		break;
	}
console.log(event);
});
</script>
</head>
<body>
<center>
<h1>VRTR-STEUERUNG</h1>
<table border="1">
<tr><td></td><td><button onmousedown="forward()" onmouseup="stop()">FORWARD</button></td><td></td></tr>
<tr><td><button onmousedown="left()" onmouseup="stop()">LEFT</button></td><td><button onmousedown="stop()" onmouseup="stop()">STOP</button></td><td><button onmousedown="right()" onmouseup="stop()">RIGHT</button></td></tr>
<tr><td></td><td><button onmousedown="backward()" onmouseup="stop()">BACKWARD</button></td><td></td></tr>
</table>
<p id="status_text"></p>
</center>
<script>
</script>
</body>
</html>
