
**1.Solving problems using array functions on the rest countries' data ([https://restcountries.com/v3.1/all](https://restcountries.com/v3.1/all)).**

a. Get all the countries from the Asia continent /region using the Filter function
```js
var xhr = new XMLHttpRequest();
xhr.open('GET', 'https://restcountries.com/v3.1/all');
xhr.responseType = 'json';
xhr.send();

xhr.onload = function(){
    var resObj = xhr.response;
    var res = resObj.filter(function(item){
    return item.continents == 'Asia';
   });
   console.log(res.map(function(item){
    return item.name.common;
   }));
}
```
**b.Get all the countries with a population of less than 2 lakhs using Filter function**
```js
var xhr = new XMLHttpRequest();
xhr.open('GET', 'https://restcountries.com/v3.1/all');
xhr.responseType = 'json';
xhr.send();

xhr.onload = function(){
    var resObj = xhr.response;
    var res = resObj.filter(function(item){
    return item.population < 200000;
   });
   console.log(res.map(function(item){
         return item.name.common;
    }));
}
```
**c.Print the following details name, capital, flag using forEach function**
```js
var xhr = new XMLHttpRequest();
xhr.open('GET', 'https://restcountries.com/v3.1/all');
xhr.responseType = 'json';
xhr.send();

xhr.onload = function(){

   var resObj = xhr.response;

   var out = [];
   resObj.forEach(function(item){
    out.push(`${item.name.common}, ${item.capital}, ${item.flag}`)
   });
   console.log(out);
}
```
**d.Print the total population of countries using reduce function**
```js
var xhr = new XMLHttpRequest();
xhr.open('GET', 'https://restcountries.com/v3.1/all');
xhr.responseType = 'json';
xhr.send();

xhr.onload = function(){
    var resObj = xhr.response;
    var population = resObj.map(function(item){
             return item.population;
            });
    var totalPopulation = population.reduce(function(a,b){
        return a+b;
    });
    console.log(`The total rest countries are ${totalPopulation}`);
}
```
**e. Print the country which uses US Dollars as currency.**
```js
var xhr = new XMLHttpRequest();
xhr.open('GET', 'https://restcountries.com/v3.1/all');
xhr.responseType = 'json';
xhr.send();

xhr.onload = function(){

   var resObj = xhr.response;
   var usd = resObj.filter((item)=>{
    return item.currencies && item.currencies.USD;
   });
   console.log(usd.map((item)=>{
    return item.name.common;
   }));
}
```
