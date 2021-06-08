<template>
  <div class="globe">
      <div id="my-globe"></div>
  </div>
</template>

<script>
import * as THREE from 'three'
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls'

export default {
  name: 'Globe',
  components: {
  },
  data () {
    return {
      camera: null,
      scene: null,
      renderer: null,
      mesh: null,
      mesh2: null,
      controls: null,
      counter: 0,
      rotate: true
    }
  },
  methods: {
    init: function () {
      // define scene
      this.scene = new THREE.Scene()
      // define renderer
      this.renderer = new THREE.WebGLRenderer({ alpha: true })
      // get Container infos
      const container = document.getElementById('my-globe')
      document.body.appendChild(container)
      var w = container.offsetWidth
      var h = container.offsetHeight
      container.appendChild(this.renderer.domElement)
      // configure renderer
      this.renderer.setSize(w, h)
      this.renderer.setPixelRatio(window.devicePixelRatio)
      // define and configure camera
      this.camera = new THREE.PerspectiveCamera(89, w / h, 2, 1000)
      this.camera.position.setZ(40)
      // sphere
      const geometry = new THREE.SphereGeometry(28, 60, 60)
      const earthTexture = new THREE.TextureLoader().load('./earth.jpeg')
      const bumpMapEarthTexture = new THREE.TextureLoader().load('./elev_bump_4k.jpeg')
      const specularMapEarthTexture = new THREE.TextureLoader().load('./water_4k.png')
      const cloudTexture = new THREE.TextureLoader().load('./fair_clouds_4k.png')
      const material = new THREE.MeshStandardMaterial({
        map: earthTexture,
        bumpMap: bumpMapEarthTexture,
        bumpScale: 0.5,
        specularMap: specularMapEarthTexture,
        specular: new THREE.Color('white')
      })
      this.mesh = new THREE.Mesh(geometry, material)

      this.mesh2 = new THREE.Mesh(
        new THREE.SphereGeometry(28.5, 60, 60),
        new THREE.MeshStandardMaterial({
          map: cloudTexture,
          bumpMap: cloudTexture,
          bumpScale: 0.1,
          transparent: true
        })
      )
      this.scene.add(this.mesh2)
      this.scene.add(this.mesh)
      this.renderer.render(this.scene, this.camera)
      const pointLight = new THREE.DirectionalLight(0xffffff, 1)
      pointLight.position.set(20, 20, 20)
      this.scene.add(new THREE.AmbientLight(0x333333))
      this.scene.add(pointLight)
      // Helpers
      // const lightHelper = new THREE.PointLightHelper(pointLight)
      // const gridHelper = new THREE.GridHelper(200, 50)
      // this.scene.add(lightHelper)
      // Controls
      this.controls = new OrbitControls(this.camera, this.renderer.domElement)
      // to disable zoom
      this.controls.enableZoom = false
      // to disable rotation
      this.controls.enableRotate = false
    },
    animate: function () {
      requestAnimationFrame(this.animate)
      if (this.rotate) {
        this.mesh.rotation.x += 0.001
        this.mesh.rotation.y -= 0.001
        this.mesh2.rotation.x += 0.001
        this.mesh2.rotation.y -= 0.001
      }
      this.renderer.render(this.scene, this.camera)
      this.controls.update()
    }
  },
  mounted () {
    this.init()
    this.animate()
  }
}

</script>

<style lang="scss" scoped>
  #my-globe{
    width:350px;
    height:350px;
    margin:auto;
    border-radius:100%;
    box-shadow: 12px 12px 15px rgba(163, 177, 198, 0.5), -6px -6px 12px rgba(163, 177, 198, 0.25), inset -6px -6px 20px rgba(163, 177, 198, 0.25), inset 6px 6px 20px rgba(163, 177, 198, 0.5);
  }
</style>
