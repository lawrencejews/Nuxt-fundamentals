<script setup>

import { computed, ref } from 'vue'

let photoGallery = ref([])

const numberOfPhotos = computed(() => {
  return photoGallery.value.length
})

const evenAlbums = computed(() => {
  return photoGallery.value.filter(item => item.albumId % 2 === 0)
})

const oddAlbums = computed(() => {
  return photoGallery.value.filter(item => !(item.albumId % 2 === 0))
})

function fetchPhotoGallery() {
  fetch("http://jsonplaceholder.typicode.com/photos")
    .then(response => response.json())
    .then(json => {
      photoGallery.value = json
    })
}

</script>

<template>
  <div class="container">
    <div class="section">
      <h1> Photo Galley</h1>
      <button @click="fetchPhotoGallery"> Fetch Data</button>
      <p> {{ numberOfPhotos }} Photos ({{ evenAlbums.length }} items albums | {{ oddAlbums.length }} odd albums)</p>
      <ul class="photo-galley-list">
        <li v-for="photo in photoGallery" :key="`photo-id-${photo.id}`">
          <img :src="photo.thumbnailUrl" />
        </li>
      </ul>
    </div>
  </div>
</template>

<style lang="scss">
@import "./node_modules/bulma/bulma.sass";

.photo-gallery-list {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
}
</style>
