<template>
  <div class="popup" :style="{top: offsetTop, left: offsetLeft}" ref="popup" v-show="selected">
    <span @click="AlertSelectedText">Selected</span>
  </div>
</template>
<script>
export default {
  data() {
    return {
      popupInitialTopOffset: 0,
      popupInitialLeftOffset: 0,
      offsetTop: 0,
      offsetLeft: "0em",
      selectedText: undefined,
      selected: false,
    };
  },
  methods: {
    ListenToDocumentSelection() {
      let sel = window.getSelection();
      setTimeout(_ => {
        if (sel && !sel.isCollapsed) {
          this.selected = true;
          this.selectedText = sel.toString();
          if (sel.rangeCount) {
            let range = sel.getRangeAt(0).cloneRange();
            if (range.getBoundingClientRect) {
              var rect = range.getBoundingClientRect();
              let left = rect.left + (rect.right - rect.left) / 2;
              let top = rect.top;

              this.offsetTop = top - this.popupInitialTopOffset - 55 + "px";

              this.offsetLeft = left - 40 - this.popupInitialLeftOffset / 2 + "px";
            }
          }
        } else {
          this.offsetLeft = "0em";
          this.selected = false;
        }
      }, 0);
    },
    AlertSelectedText() {
      alert(`"${this.selectedText}" selected`);
    }
  },
  mounted() {
    this.popupInitialTopOffset = this.$refs.popup.offsetHeight;
    this.popupInitialLeftOffset = this.$refs.popup.offsetWidth;
    window.addEventListener("mouseup", this.ListenToDocumentSelection);
  },
  destroyed() {
    window.removeEventListener("mouseup", this.ListenToDocumentSelection);
  }
};
</script>
<style scoped>
.popup {
  position: absolute;
  color: #FFF;
  background-color: #000;
  padding: 10px;
  border-radius: 5px;
  transform-origin: center, center;
  cursor: pointer;
}
.popup:after {
  content: "";
  border-bottom: 5px solid #000;
  border-right: 5px solid #000;
  border-top: 5px solid transparent;
  border-left: 5px solid transparent;
  position: absolute;
  top: calc(100% - 5px);
  transform: rotate(45deg);
  left: calc(50% - 3px);
}
</style>
