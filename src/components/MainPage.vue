<template>
  <div class="mainPageRoot">
    <div class="buttonsZone">
      <image-button
        caption="New game"
        @click="startGame"
        src="/assets/racing-flag.svg"
        width="50px"
      />
      <image-button
        caption="Stop game"
        @click="stopGame"
        src="/assets/stop.svg"
        width="50px"
      />
    </div>

    <loloof64-chessboard
      class="chessboard"
      ref="chessboard"
      size="400"
      left="250"
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
  </div>
</template>

<script>
import { ref } from "vue";
import ImageButton from "./ImageButton";

import '@loloof64/chessboard-component/dist/index';

export default {
  setup() {
    const chessboard = ref(null);

    const startGame = () => {
      if (chessboard.value != null) chessboard.value.newGame();
    };

    const stopGame = () => {
      if (chessboard.value != null) chessboard.value.stop();
    };

    return { chessboard, startGame, stopGame };
  },
  components: {
    ImageButton,
  },
};
</script>

<style scoped>
.mainPageRoot {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
}
.buttonsZone {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  margin: 10px;
}

.imgButtonRoot {
  margin: 0 5px;
}
</style>
