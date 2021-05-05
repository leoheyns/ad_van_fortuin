<template>
  <div class="board" border="black">
    <table class="table center is-bordered">
      <tbody>
        <tr v-for="(row, rowI) in rows" v-bind:key="rowI">
          <boardCell
            v-for="(cell, index) in row"
            :cell="cell"
            :key="index">
          </boardCell>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>

import boardCell from "./boardCell.vue"

export default {
    props: {
      lines: Array,
      revealed: String,
    },
    components: {
        boardCell
    },
    methods: {
      rowify(string, max_length){
        var add_length = max_length - string.length + 1
        var row = string.split('').map(s => {return {letter: s, revealed: this.revealed}}).concat(new Array(add_length).fill({letter: " ", revealed: ""}))
        row.unshift({letter: " ", revealed: " "})
        return row;
      }
    },
    computed: {
      rows() {
        var max_length = this.lines.map(l => l.length).reduce(function(a, b) {
          return Math.max(a, b);
        })
        if (max_length){
          var result = this.lines.map(l => this.rowify(l, max_length))
          return result
        }
        else{
          return []
        }
      }
    }
}
</script>

<style lang="scss" scoped>
table.center {
    margin-left:auto; 
    margin-right:auto;
}
</style>

