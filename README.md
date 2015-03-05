# Javascript_event_practice
Deep understanding and practice of core javascript event mechanism on JTDG(6th Edition) 

Closure Problem used in this practice:



document.addEventListener('DOMContentLoaded', function () {
  *****
  for (var i = 0, len = 100; i < len; i++) {
    var div = document.createElement('div');
    div.innerHTML = 'This is div ' + (i + 1); // common closure error
  }
  *****
});// get 100 div, innerHTML ranging from 1 to 100

Take a difference example I could think:

for(var i = 0; i < 10; i++) {
    setTimeout(function() {
        console.log(i);
    }, 1000);
}// get 10 10 times

Reason: setTimeout is asynchronized function, loop has finished running but i still exists due to declaration 
inside function are preposed to first line.

Solution: create a new closure

for (var i = 0; i < 10; i++) {
       setTimeout(fn(i), 1000);
   }
   function fn() {
       var a = arguments[0];
       return function() {
           console.log(a); //
       };
   }
   
