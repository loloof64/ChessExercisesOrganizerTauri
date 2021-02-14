<template>
    <loloof64-chessboard
        class="chessboard"
        ref="chessboard"
        size="400"
        background="crimson"
        coordinates_color="yellow"
        white_cell_color="navajowhite"
        black_cell_color="peru"
        reversed="false"
        origin_cell_color="red"
        target_cell_color="green"
        dnd_cross_color="purple"
        white_player_human="true"
        black_player_human="true"
        move_highlight_color="red"
        last_move_visible="true"
        coordinates_visible="true"
    ></loloof64-chessboard>
    <button @click="startGame">New game</button>
</template>

<script>
import {ref} from 'vue';

export default {
    setup() {
        const chessboard = ref(null);

        const startGame = () => {
            if (chessboard.value != null) chessboard.value.newGame();
        }

        return {chessboard, startGame};
    }
}
</script>

<style scoped>
.chessboard {
    display: inline-block;
}
</style>