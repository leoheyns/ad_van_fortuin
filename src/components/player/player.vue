<template>
    <div>
        <div class="box">
            pleur hier webcam <br/><br/><br/>
        </div>
        <div v-if="turn" class="is-size-3 has-background-success">
            {{name}}
        </div>
        <div v-else class="is-size-3">
            {{name}}
        </div>
        <div>
            <table class="table center">
                <tbody>
                    <tr>
                        <td v-for="(i, index) in 4" v-bind:key="index">
                            <img v-if="i * 8 <= sips" src="https://i.imgur.com/9u4oLuB.png" width="30" height="30"/>
                            <img v-else-if="i * 8 - 4 <= sips" src="https://i.imgur.com/DbkYVd8.png" width="30" height="30"/>
                            <img v-else src="https://i.imgur.com/B99vC6s.png" width="30" height="30"/>
                        </td>
                    </tr>
                    <tr>
                        <td v-for="(i, index) in 4" v-bind:key="index">
                            <img v-if="(9 - i) * 8 <= sips" src="https://i.imgur.com/9u4oLuB.png" width="30" height="30"/>
                            <img v-else-if="(9 - i) * 8 - 4 <= sips" src="https://i.imgur.com/DbkYVd8.png" width="30" height="30"/>
                            <img v-else src="https://i.imgur.com/B99vC6s.png" width="30" height="30"/>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
  <!-- <td v-bind:class="[is_letter(cell) ? 'letter' : '']">
    <span v-if="cell.revealed.includes(cell.letter)">{{cell.letter}}</span>
  </td> -->
</template>

<script>
  export default {
    name: 'player',
    props: {
        sips: {
        type: [Object, Number],
        required: true
      }, name: {
        type: [Object, String],
        required: true
      },
      turn: {
        type: [Object, Boolean],
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
//   table td {
//     border: .1rem solid #000000;
//     padding: .5rem;
//     width: 1.5rem;
//     height: 1.5rem;
//     text-align: center;
//     font-weight: bold;
//     background: #109010;
//   }

table.center {
    margin-left:auto; 
    margin-right:auto;
}
</style>