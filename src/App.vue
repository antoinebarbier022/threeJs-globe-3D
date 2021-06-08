<template>
  <div id="app">
    <h1>Our beautiful planet</h1>
    <Globe/>
    <div v-if="false" class="container-buttons">
      <Button title="Affrique"/>
      <Button title="Europe"/>
      <Button title="Asie"/>
      <Button title="Amérique"/>
      <Button title="Océanie"/>
      <Button title="Antartique"/>
    </div>
    <Footer/>
  </div>
</template>

<script>
import Button from '@/components/Button.vue'
import Globe from '@/components/Globe.vue'
import Footer from '@/components/Footer.vue'

export default {
  name: 'App',
  components: {
    Globe, Button, Footer
  }
}
</script>

<style lang="scss">

$background: #E0E5EC;

html, body{
  margin:0;
  padding:0;
  background: $background;
}
h1{
  font-family: reenie-beanie, sans-serif;
  font-size: 54pt;
  font-weight: 500;
  font-style: normal;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
button, a, p{
  color: #2c3e50;
}
.container-buttons{
  max-width: 600px;
  padding:0px 40px 40px 40px;
  margin:auto;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
}

@media (max-width:800px) {
  h1{
  font-size: 45pt;
  }
}

@media (max-width:600px) {
  h1{
  font-size: 35pt;
  }
}

@media (max-width:400px) {
  h1{
  font-size: 30pt;
  }
}
</style>
