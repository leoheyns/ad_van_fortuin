<template>
  <td v-bind:class="[is_letter(cell) ? 'letter' : '']">
    <span v-if="cell.revealed.includes(cell.letter)" class = "is-size-2">{{cell.letter}}</span>
  </td>
</template>

<script>
  export default {
    name: 'bingoTicketCell',
    props: {
      cell: {
        type: [Object, Number],
        required: true
      },
    },
    methods: {
        is_letter(cell) {
            return cell.letter !== " "
        }
    }
  }
</script>

<style lang="scss" scoped>
  table td {
    border: .1rem solid #000000;
    padding: .5rem;
    width: 70px;
    height: 70px;
    text-align: center;
    font-weight: bold;
    background: #109010;


    &.letter {
      background: #ffffff;
      color: #000000;
      font-weight: bold;
    }
  }
</style>