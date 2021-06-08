<template>
  <button id="button">
    {{ title }}
  </button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    title: String
  },
  components: {
  }
}

</script>

<style lang="scss" scoped>
  button{
    width:150px;
    background: #E0E5EC;
    border-radius : 10px;
    padding: 10px 40px 10px 40px;
    margin: 10px;
    border:none;
    box-shadow: 0px 4px 4px rgba(163, 177, 198, 0.5), inset 4px 4px 4px rgba(163, 177, 198, 0.25);
    border-radius: 12px;
    font-size: 11pt;
    font-weight: 700;
  }
  button:focus{
      box-shadow: inset 0px 2px 2px rgba(163, 177, 198, 0.5),  2px 2px 2px rgba(163, 177, 198, 0.25);
  }

</style>
