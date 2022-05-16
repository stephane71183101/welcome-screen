<template v-bind:style="{ 'background-color': color}">
  <div id="app">
    <main>
      <h1>Welcome to Opportunity</h1>
      <p id="date">11.03.1944</p>
      
      <ul>
        <li id="listBox">
          <span>14.00 Uhr</span>
          <h3>Bäftigung Besuch</h3>
          <span>Interessierte für den zweiten Kurs werden uns besuchen</span>
          </li>
      </ul>

      <footer>
        <p>footer</p>
        <img>
        <img>
        <img>
      </footer>
    </main>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
return {
}
}
}
</script>

<style>
@font-face {
  font-family: 'Inter';
  src: url('~@/assets/Inter-VariableFont_slnt,wght.ttf');
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;

}

body {
  font-family: 'Inter', sans-serif;
}

h1 {
position: absolute;
width: 764px;
height: 75px;
left: 60px;
top: 69px;
font-family: 'Inter';
font-style: normal;
font-weight: 900;
font-size: 62px;
line-height: 75px;
color: #323D4A;
}

ul {
position: absolute;
left: 5.5vw;
right: 5.5vw;
top: 20.33%;
bottom: 20.33%;
background: #0F05A0;
}

#date {
position: absolute;
width: 335px;
height: 75px;
left: 60px;
top: 165px;
font-family: 'Inter';
font-style: normal;
font-weight: 500;
font-size: 62px;
line-height: 75px;
color: #9AA7B1;
}

#app {
  background-color:#E8EFF4;

}

main {
  min-height: 100vh;
  margin-left: 5.5vw;
  margin-right: 5.5vw;
}

footer {
  position: fixed;
  background-color: white;
}
</style>
