<template>
  <div ref="container" class="three-container"></div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import * as THREE from 'three'

const container = ref(null)
let scene, camera, renderer, particles, animationId

onMounted(() => {
  scene = new THREE.Scene()
  camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000)
  renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true })
  renderer.setSize(window.innerWidth, window.innerHeight)
  renderer.setPixelRatio(2)
  container.value.appendChild(renderer.domElement)

  const count = 6000
  const positions = new Float32Array(count * 3)
  const colors = new Float32Array(count * 3)

  for (let i = 0; i < count; i++) {
    positions[i*3] = (Math.random() - 0.5) * 25
    positions[i*3+1] = (Math.random() - 0.5) * 25
    positions[i*3+2] = (Math.random() - 0.5) * 25
    colors[i*3] = Math.random() * 0.5 + 0.5
    colors[i*3+1] = Math.random() * 0.3
    colors[i*3+2] = Math.random() * 0.5 + 0.5
  }

  const geo = new THREE.BufferGeometry()
  geo.setAttribute('position', new THREE.BufferAttribute(positions, 3))
  geo.setAttribute('color', new THREE.BufferAttribute(colors, 3))

  const mat = new THREE.PointsMaterial({
    size: 0.04,
    vertexColors: true,
    transparent: true,
    opacity: 0.6,
    blending: THREE.AdditiveBlending
  })

  particles = new THREE.Points(geo, mat)
  scene.add(particles)
  camera.position.z = 8

  const animate = () => {
    animationId = requestAnimationFrame(animate)
    particles.rotation.y += 0.0003
    particles.rotation.x += 0.0001
    renderer.render(scene, camera)
  }
  animate()

  window.addEventListener('resize', handleResize)
})

const handleResize = () => {
  camera.aspect = window.innerWidth / window.innerHeight
  camera.updateProjectionMatrix()
  renderer.setSize(window.innerWidth, window.innerHeight)
}

onUnmounted(() => {
  cancelAnimationFrame(animationId)
  window.removeEventListener('resize', handleResize)
  if (container.value?.contains(renderer.domElement)) {
    container.value.removeChild(renderer.domElement)
  }
})
</script>

<style scoped>
.three-container {
  position: fixed; top: 0; left: 0;
  width: 100%; height: 100%;
  z-index: 0; pointer-events: none;
}
</style>
