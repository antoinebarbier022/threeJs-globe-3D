<template>
    <div class="footer">
        <p>Website created by <a href="https://www.antoinebarbier.fr">Antoine Barbier</a> with <a class="link-technologie" href="https://vuejs.org/" target="_blank">VueJs</a> and <a class="link-technologie" href="https://threejs.org/" target="_blank">ThreeJs</a></p>
    </div>
</template>

<script>
export default {
  name: 'Footer'
}
</script>

<style lang="scss">
.footer{
    position: fixed;
    width:100%;
    bottom:10px;
    margin:auto;
    display:flex;
    justify-content: center;
    align-items: center;
    height: 20px;
    p{
        width:100%;
    }
    a{
        font-weight: bold;
    }
    .link-technologie{
        text-decoration: none;
        color: rgb(1, 87, 138);
        // color: rgb(79, 119, 80);
    }
}
</style>
