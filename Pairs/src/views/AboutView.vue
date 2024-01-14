<template>
  <div class="about">
    <h1>This is an about page</h1>

    <div class="contaner">
      <div
        v-for="(item, index) in PictureArray"
        :key="index"
        :class="`item item_${index}`"
        v-on:click="sentToCompare"
        :style="{
          backgroundImage: `url(${item})`
        }"
      ></div>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'

// ARRAYS
const compare = reactive({
  cards: []
})

let matchedArr = []

let arr = [
  'https://c3.klipartz.com/pngpicture/577/216/sticker-png-tekken-7-king-tekken-character-thumbnail.png',
  'https://w7.pngwing.com/pngs/557/517/png-transparent-tekken-6-bloodline-rebellion-ling-xiaoyu-tekken-3-tekken-king-orange-video-game.png',
  'https://e7.pngegg.com/pngimages/1015/905/png-clipart-tekken-6-tekken-tag-tournament-2-tekken-3-tekken-7-tekken-king-video-game.png',
  'https://c3.klipartz.com/pngpicture/577/216/sticker-png-tekken-7-king-tekken-character-thumbnail.png',
  'https://w7.pngwing.com/pngs/557/517/png-transparent-tekken-6-bloodline-rebellion-ling-xiaoyu-tekken-3-tekken-king-orange-video-game.png',
  'https://e7.pngegg.com/pngimages/1015/905/png-clipart-tekken-6-tekken-tag-tournament-2-tekken-3-tekken-7-tekken-king-video-game.png'
]

const PictureArray = ref(arr)

// FUNCTIONS

function sentToCompare(event) {
  if (!checkMantched(event.target.style.backgroundImage.slice(4, -1).replace(/"/g, ''))) {
    compare.cards.push([
      event.target.style.backgroundImage.slice(4, -1).replace(/"/g, ''),
      event.target.className
    ])
    event.target.style.webkitFilter = 'brightness(1)'

    if (compare.cards.length > 1) {
      if (
        compare.cards[1][1] !== compare.cards[0][1] &&
        compare.cards[1][0] === compare.cards[0][0]
      ) {
        // add the address to the matches array
        matchedArr.push(compare.cards[1][0])
        compare.cards = []
        console.log('есть совпадение')
      } else {
        let firstCard = document.querySelector(`.${compare.cards[0][1].slice(5)}`)
        let secondCard = document.querySelector(`.${compare.cards[1][1].slice(5)}`)
        setTimeout(() => {
          firstCard.style.webkitFilter = 'brightness(0)'
          secondCard.style.webkitFilter = 'brightness(0)'
        }, 500)

        compare.cards = []
      }
    }
  }
}
function shuffle(array) {
  array.sort(() => Math.random() - 0.5)
}

shuffle(arr)

function checkMantched(url) {
  return matchedArr.includes(url)
}
</script>

<style>
.contaner {
  border: thick double #32a1ce;
  display: grid;
  grid-template-columns: 100px 100px 100px;
  grid-template-rows: 200px 200px;

  gap: 5px;

  justify-content: center;
}

.item {
  filter: brightness(0);
  background: linear-gradient(rgba(0, 0, 255, 0.5), rgba(255, 255, 0, 0.5));
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  background-blend-mode: normal;
}

@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
