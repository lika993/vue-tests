<template>
  <div id="app">
    
    <ul  class="menu menu_reversed blink-text-menu">
      <li><a href="https://vuejs.org" target="_blank">Home</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank">Skills</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank">Works</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank">Contacts</a></li>
    </ul>
    <div class="wrapper">
      <p class="text">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Cum, libero, explicabo. At modi quis, eum necessitatibus rem iste velit officiis non beatae! Illo quis repellendus similique repellat, id nam sequi.   ddddddddddddddddddddd</p>
    </div>
   
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }, mounted(){

    let  blinkTextMenuLinks = document.querySelectorAll(".blink-text-menu li a");
blinkTextMenuLinks.forEach(function (link) {
console.log(link)
  let  letters = link.textContent.split("");
  //делим на буквы - получаем массив букв
  link.textContent = "";
  letters.forEach(function (letter, i) {
    //считаем количество символов в выражении, начиная с 1
    i += 1;
    let  span = document.createElement("span");
    let  delay = i / 20;
    if (i % 2 === 0) {
      delay -= 0.1;
    } else
    {
      delay += 0.05;
    }
    let  letterOut = document.createElement("span");
    letterOut.textContent = letter;
    letterOut.style.transitionDelay = delay + "s";
    letterOut.classList.add("out");
    span.append(letterOut);
    let  letterIn = document.createElement("span");
    letterIn.textContent = letter;
    letterIn.style.transitionDelay = delay + "s";
    letterIn.classList.add("in");
    span.append(letterIn);
    link.append(span);
    
  });
});
let wrapper = document.querySelector(".wrapper");
let text = document.querySelector(".text");

let textCont = text.textContent;
text.style.display = "none";

for (let i = 0; i < textCont.length; i++) {
  (function(i) {
    setTimeout(function() {
      // Created textNode to append
      let texts = document.createTextNode(textCont[i])
      let spanA = document.createElement('span');
      spanA.appendChild(texts);

      spanA.classList.add("wave");
      wrapper.appendChild(spanA);

    }, 75 * i);
  }(i));
}
  }
}

</script>

<style lang="scss">

body {

  background: #1A1E23;
}
.text{
  color: #fff;
}
.blink-text-menu {
  display: flex;
  list-style-type: none;
}
.blink-text-menu li a {
  position: relative;
  display: flex;
  padding: 6px;
  color: white;
  font-family: Lato, sans-serif;
  text-decoration: none;
}
.blink-text-menu li a span {
  position: relative;
  overflow: hidden;
  transition: 0.6s;
}
.blink-text-menu li a span .out {
  display: inline-flex;
}
.blink-text-menu li a span .in {
  position: absolute;
  left: 0;
  opacity: 0;
  transform: translateX(100%);
}
.blink-text-menu li a:hover span .out {
  opacity: 0;
  transform: translateX(-100%);
}
.blink-text-menu li a:hover span .in {
  opacity: 1;
  transform: translateX(0);
}
.wave {
 color: #8fc8ae;
}

</style>
