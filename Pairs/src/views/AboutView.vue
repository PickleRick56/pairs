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

// Functions

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
        //находим элемент по классу
        let firstCard = document.querySelector(`.${compare.cards[0][1].slice(5)}`)
        let secondCard = document.querySelector(`.${compare.cards[1][1].slice(5)}`)

        document.querySelector(`.${compare.cards[0][1].slice(5)}`).removeAttribute('onclick')
        document.querySelector(`.${compare.cards[1][1].slice(5)}`).removeAttribute('onclick')

        // найденому элементу меняем класс на класс с датой
        firstCard.className = `${compare.cards[0][1]}`

        secondCard.className = `${compare.cards[1][1]}`

        // записываем новый класс элемента в массив
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

  // console.log((event.target.style.webkitFilter = 'brightness(1)'))
  // console.log(event.target.style.backgroundImage.slice(4, -1).replace(/"/g, ''))
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
  /* grid-template-areas: 'a a a' 'b c c' 'b c c'; */
  gap: 5px;
  /* justify-items: center;
  align-items: start; */
  justify-content: center;
  /* grid-auto-flow: column; */
}

.item {
  /* height: 50px;
  width: 40px; */
  filter: brightness(0);
  background: linear-gradient(rgba(0, 0, 255, 0.5), rgba(255, 255, 0, 0.5));
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  background-blend-mode: normal;
}
.item_0 {
  /* justify-self: center;
  align-self: center; */
  /* 
  background-image: linear-gradient(rgba(0, 0, 255, 0.5), rgba(255, 255, 0, 0.5)),
    url('https://w7.pngwing.com/pngs/557/517/png-transparent-tekken-6-bloodline-rebellion-ling-xiaoyu-tekken-3-tekken-king-orange-video-game.png');
   */
}
.item_1 {
  /* justify-self: center;
  align-self: center; */

  /* background-image: linear-gradient(rgba(0, 0, 255, 0.5), rgba(255, 255, 0, 0.5)),
    url('https://e7.pngegg.com/pngimages/149/227/png-clipart-tekken-5-dark-resurrection-tekken-4-ling-xiaoyu-kazuya-mishima-tekken-video-game-shoe.png'); */
}
.item_2 {
  /* justify-self: center;
  align-self: center; */

  /* background-image: linear-gradient(rgba(0, 0, 255, 0.5), rgba(255, 255, 0, 0.5)),
    url('https://e7.pngegg.com/pngimages/149/227/png-clipart-tekken-5-dark-resurrection-tekken-4-ling-xiaoyu-kazuya-mishima-tekken-video-game-shoe.png'); */
}
.item_3 {
  /* justify-self: center;
  align-self: center; */

  /* background-image: linear-gradient(rgba(0, 0, 255, 0.5), rgba(255, 255, 0, 0.5)),
    url('https://e7.pngegg.com/pngimages/149/227/png-clipart-tekken-5-dark-resurrection-tekken-4-ling-xiaoyu-kazuya-mishima-tekken-video-game-shoe.png'); */
}
.item_4 {
  /* justify-self: center;
  align-self: center; */

  /* background-image: linear-gradient(rgba(0, 0, 255, 0.5), rgba(255, 255, 0, 0.5)),
    url('https://e7.pngegg.com/pngimages/149/227/png-clipart-tekken-5-dark-resurrection-tekken-4-ling-xiaoyu-kazuya-mishima-tekken-video-game-shoe.png'); */
}
.item_5 {
  /* justify-self: center;
  align-self: center; */

  /* background-image: linear-gradient(rgba(0, 0, 255, 0.5), rgba(255, 255, 0, 0.5)),
    url('https://e7.pngegg.com/pngimages/149/227/png-clipart-tekken-5-dark-resurrection-tekken-4-ling-xiaoyu-kazuya-mishima-tekken-video-game-shoe.png'); */
}

@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
