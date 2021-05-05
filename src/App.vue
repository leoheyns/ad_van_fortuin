<template>
  <div id="app">
    <div class="columns">
      <div v-for="(p, index) in players" v-bind:key="index" class="column is-3">
        <player :sips="p.sips" :name="p.name" :turn="is_turn(index)"/>
      </div>
    </div>
    <div clss="columns">
      <board lass="column is-12"
        :lines="lines"
        :revealed="revealed"
      />
    </div>
    <input type="text" @change="add_points" v-model="revealed"/>
    <p>number of sips</p>
    <input type="radio" id="one" value="1" v-model="sips_selected">
    <label for="1">One</label>
    <br>
    <input type="radio" id="two" value="2" v-model="sips_selected">
    <label for="2">Two</label>
    <br>
    <input type="radio" id="three" value="3" v-model="sips_selected">
    <label for="3">Three</label>
    <br>
    <input type="radio" id="four" value="4" v-model="sips_selected">
    <label for="4">Four</label>
    <br>

    <button @click="change_turn"> change turn </button>
    <button @click="finish_word"> finnish word </button>
  </div>
</template>

<script>
import board from './components/board.vue'
import player from './components/player/player.vue'

export default {
  name: 'App',
  data() {
    return {
      lines: ["wie dit", "leest trekt", "een ad"],
      revealed: "",
      players: [{name: "henk", sips: 0}, {name: "piet", sips: 0}, {name: "sjaak", sips: 0}, {name: "jens", sips: 0}],
      turn: 0,
      sips_selected: 1,
    }
  },
  components: {
    board,
    player
  },
  methods: {
    is_turn(n) {
      return n == this.turn
    },
    add_points() {
      var c = this.revealed.slice(-1);
      if (!"aeoui ".includes(c)){
        this.players[this.turn].sips += ((this.lines.join('')).split(c).length - 1) * this.sips_selected
      }
    },
    finish_word() {
      this.players[this.turn].sips += 16
    },
    change_turn() {
      this.turn = (this.turn + 1) % this.players.length
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>