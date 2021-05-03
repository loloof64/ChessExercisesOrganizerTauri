<template>
  <div class="imgButtonRoot" @click="clickEvent" ref="rootElemRef">
    <img :src="src" ref="imgElemRef" />
    <div ref="captionElemRef">{{ caption }}</div>
  </div>
</template>

<script>
import { ref, onMounted } from "vue";
export default {
  props: {
    src: {
      type: String,
      required: true,
    },
    caption: {
      type: String,
      default: "",
    },
    width: {
      type: String,
      required: true,
    },
  },
  setup(props, context) {
    const rootElemRef = ref();
    const imgElemRef = ref();
    const captionElemRef = ref();

    onMounted(function() {
      const rootElem = rootElemRef.value;
      rootElem.style.width = props.width;

      const imgElem = imgElemRef.value;
      imgElem.style.width = props.width;
      imgElem.style.height = props.width;

      const captionElem = captionElemRef.value;
      captionElem.style.width = props.width;
    });

    function clickEvent() {
      context.emit("click");
    }

    return {
      rootElemRef,
      imgElemRef,
      captionElemRef,
      clickEvent,
    };
  },
};
</script>

<style scoped>
.imgButtonRoot {
  border: 1px solid black;
  padding: 5px;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
}
</style>
