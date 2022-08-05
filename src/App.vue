<script>
import './assets/css/app/app.css';

export default {
  setup() {
    const getImg = (name) => {
      return new URL(`./assets/img/${name}.png`, import.meta.url).href
    }
    return {getImg}
  },
  data() {
    return {
      id: 0,
      init: null,
      words: [
        {
          id: 1,
          english: 'happy',
          serbian: 'srećna',
          imgURL: 'happy'
        }, {
          id: 2,
          english: 'nice',
          serbian: 'lijepo',
          imgURL: 'nice'
        }, {
          id: 3,
          english: 'friend',
          serbian: 'prijatelju',
          imgURL: 'friend'
        }, {
          id: 4,
          english: 'explosion',
          serbian: 'eksplozija',
          imgURL: 'explosion'
        }, {
          id: 5,
          english: 'carrot',
          serbian: 'šargarepa',
          imgURL: 'carrot'
        }, {
          id: 6,
          english: 'car',
          serbian: 'auto',
          imgURL: 'car'
        }, {
          id: 7,
          english: 'soldier',
          serbian: 'vojnik',
          imgURL: 'soldier'
        }, {
          id: 8,
          english: 'fear',
          serbian: 'strah',
          imgURL: 'fear'
        }, {
          id: 9,
          english: 'relativity',
          serbian: 'relativnost',
          imgURL: 'relativity'
        }, {
          id: 10,
          english: 'book',
          serbian: 'knjiga',
          imgURL: 'book'
        }, {
          id: 11,
          english: 'Earth',
          serbian: 'Zemlja',
          imgURL: 'earth'
        }, {
          id: 12,
          english: 'speed limit',
          serbian: 'ograničenje brzine',
          imgURL: 'speed_limit'
        },
        {
          id: 12,
          english: 'speed limit',
          serbian: 'ograničenje brzine',
          imgURL: 'speed_limit'
        }
      ],
      answers: {
        right: [],
        wrong: []
      },
      counter: 0
    }
  },
  methods: {
    separate() {
      if (this.init === this.words[this.counter].serbian
          || this.init === this.words[this.counter].english) {
        this.answers.right.push(this.words[this.counter])
        this.counter++
      } else {
        this.answers.wrong.push(this.words[this.counter])
        this.counter++
      }
    }
  }
}
</script>

<template>
  <div class="container">
    <img class="logo" src="./assets/logo.png" alt="logo">
    <!--    content-->
    <div class="wrapper">
      <img class="main-img"
           :src="getImg(words[this.counter].imgURL)"
           :alt="words[this.counter].english"/>

      <p class="main-title">
        {{ new Date().getTime() / 2 % 1 ? words[this.counter].english : words[this.counter].serbian }}</p>
      <input
          @keyup.enter="separate"
          v-model="init"
          class="main-input"
          type="text">
      <br/>
      <button
          @click="separate"
          :disabled="counter===12"
          class="main-btn">Let's see
      </button>

      <!--      result-->
      <div class="result">
        <div class="left">
          <img src="./assets/like.png" alt="like">
          <p> {{ answers.right.length }} / 12</p>
        </div>
        <div class="right">
          <img src="./assets/dislike.png" alt="dislike">
          <p>{{ answers.wrong.length }} / 12</p>
        </div>
      </div>

    </div>
  </div>
</template>