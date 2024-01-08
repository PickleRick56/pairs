<template>
  <div class="about">
    <h1>This is an about page</h1>

    <div class="contaner">
      <div
        v-for="(item, index) in PictureArray"
        :key="index"
        class="item item_1"
        :style="{
          backgroundImage: `url(${item})`
        }"
      ></div>
      <!-- <div class="item item_1">1</div>
      <div class="item item_2">2</div>
      <div class="item item_3">3</div>
      <div class="item item_4">4</div>
      <div class="item item_5">5</div>
      <div class="item item_6">6</div> -->
    </div>
  </div>
  <div
    v-for="(item, index) in PictureArray"
    :key="index"
    class="thing"
    :style="{
      backgroundImage: `url(${item})`,

      width: '200px',
      height: '300px'
    }"
  ></div>
</template>

<script setup>
import { ref } from 'vue'
let arr = [
  'https://c3.klipartz.com/pngpicture/577/216/sticker-png-tekken-7-king-tekken-character-thumbnail.png',
  'https://w7.pngwing.com/pngs/557/517/png-transparent-tekken-6-bloodline-rebellion-ling-xiaoyu-tekken-3-tekken-king-orange-video-game.png',
  'https://e7.pngegg.com/pngimages/1015/905/png-clipart-tekken-6-tekken-tag-tournament-2-tekken-3-tekken-7-tekken-king-video-game.png',
  'https://c3.klipartz.com/pngpicture/577/216/sticker-png-tekken-7-king-tekken-character-thumbnail.png',
  'https://w7.pngwing.com/pngs/557/517/png-transparent-tekken-6-bloodline-rebellion-ling-xiaoyu-tekken-3-tekken-king-orange-video-game.png',
  'https://e7.pngegg.com/pngimages/1015/905/png-clipart-tekken-6-tekken-tag-tournament-2-tekken-3-tekken-7-tekken-king-video-game.png'
]
const PictureArray = ref(arr)

function shuffle(array) {
  array.sort(() => Math.random() - 0.5)
}
shuffle(arr)
</script>

<style>
.contaner {
  border: thick double #32a1ce;
  display: grid;
  grid-template-columns: 100px 100px 100px;
  grid-template-rows: 200px 200px;
  /* grid-template-areas: 'a a a' 'b c c' 'b c c'; */
  gap: 5px;
  /* justify-items: center;
  align-items: start; */
  justify-content: center;
  /* grid-auto-flow: column; */
}
.thing {
  height: 50px;
  width: 40px;
  background-color: red;
  background-size: contain;
}
.item {
  /* height: 50px;
  width: 40px; */
  background: linear-gradient(rgba(0, 0, 255, 0.5), rgba(255, 255, 0, 0.5));
}
.item_1 {
  /* justify-self: center;
  align-self: center; */

  background-image: linear-gradient(rgba(0, 0, 255, 0.5), rgba(255, 255, 0, 0.5)),
    url('https://w7.pngwing.com/pngs/557/517/png-transparent-tekken-6-bloodline-rebellion-ling-xiaoyu-tekken-3-tekken-king-orange-video-game.png');
  background-size: contain;
  background-position: center;
  background-repeat: no-repeat;
  background-blend-mode: normal;
}
.item_2 {
  /* justify-self: center;
  align-self: center; */

  background-image: linear-gradient(rgba(0, 0, 255, 0.5), rgba(255, 255, 0, 0.5)),
    url('https://e7.pngegg.com/pngimages/149/227/png-clipart-tekken-5-dark-resurrection-tekken-4-ling-xiaoyu-kazuya-mishima-tekken-video-game-shoe.png');
  background-size: contain;
  background-position: center;
  background-repeat: no-repeat;
}
.item_3 {
  /* justify-self: center;
  align-self: center; */

  background-image: linear-gradient(rgba(0, 0, 255, 0.5), rgba(255, 255, 0, 0.5)),
    url('https://e7.pngegg.com/pngimages/149/227/png-clipart-tekken-5-dark-resurrection-tekken-4-ling-xiaoyu-kazuya-mishima-tekken-video-game-shoe.png');
  background-size: contain;
  background-position: center;
  background-repeat: no-repeat;
}
.item_4 {
  /* justify-self: center;
  align-self: center; */

  background-image: linear-gradient(rgba(0, 0, 255, 0.5), rgba(255, 255, 0, 0.5)),
    url('https://e7.pngegg.com/pngimages/149/227/png-clipart-tekken-5-dark-resurrection-tekken-4-ling-xiaoyu-kazuya-mishima-tekken-video-game-shoe.png');
  background-size: contain;
  background-position: center;
  background-repeat: no-repeat;
}
.item_5 {
  /* justify-self: center;
  align-self: center; */

  background-image: linear-gradient(rgba(0, 0, 255, 0.5), rgba(255, 255, 0, 0.5)),
    url('https://e7.pngegg.com/pngimages/149/227/png-clipart-tekken-5-dark-resurrection-tekken-4-ling-xiaoyu-kazuya-mishima-tekken-video-game-shoe.png');
  background-size: contain;
  background-position: center;
  background-repeat: no-repeat;
}
.item_6 {
  /* justify-self: center;
  align-self: center; */

  background-image: linear-gradient(rgba(0, 0, 255, 0.5), rgba(255, 255, 0, 0.5)),
    url('https://e7.pngegg.com/pngimages/149/227/png-clipart-tekken-5-dark-resurrection-tekken-4-ling-xiaoyu-kazuya-mishima-tekken-video-game-shoe.png');
  background-size: contain;
  background-position: center;
  background-repeat: no-repeat;
}

@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
