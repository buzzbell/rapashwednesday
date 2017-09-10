<template>
  <div class="p2" id="app">
    <router-view></router-view>
    <div class='footer center p3'>
      Contact:<br><a href="mailto:ashwednesdaymgmt@gmail.com">ashwednesdaymgmt@gmail.com</a>
    </div>
  </div>
</template>

<script>

export default {
  name: 'app'
}
</script>

<style>
#app {
  font-family: 'Arimo', sans-serif;
  color: #2c3e50;
  margin: 0 auto;
  margin-top: 60px;
  max-width: 900px;
}

h1, h2, h3 {
  color: rgb(108, 216, 255);
  font-family: 'Permanent Marker', cursive;
}

h1 {
  font-size: 4.5rem;
  text-shadow: -3px -3px rgb(247, 221, 73);
  margin-bottom: 0;
  text-align: center;
  letter-spacing: .25rem;
}

h2 {
  font-size: 3rem;
  text-align: center;
}

p {
  line-height: 1.5rem;
}

.banner-box {
  background-color: #4D4689;
  color: white;
  padding: 15px;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  text-align: center;
}
.banner-box > a {
  color: white;
}
</style>
