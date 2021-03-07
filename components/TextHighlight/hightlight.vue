<template>
  <div class="absolute cursor-pointer" @click="AlertSelectedText" :style="{top: offsetTop, left: offsetLeft}" ref="popup" v-show="selected">
    <svg width="48" height="48" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M0 6a6 6 0 016-6h36a6 6 0 016 6v26a6 6 0 01-6 6h-4.9L24 48 10.9 38H6a6 6 0 01-6-6V6z" fill="#292929"/><g clip-path="url(#clip0)" fill="#fff"><path d="M29 25.3h-4.5a.5.5 0 100 1H29a.5.5 0 000-1zM18 23.5l-1.9 2c-.3.2 0 .7.4.7h3l.3-.1.4-.4-2.1-2.2zM19.3 19.7c-.5.6-.7 1.4-.5 2.1l-.1 1L21 25h1c.7.1 1.4 0 2-.6l-4.7-4.7zM31.5 13.8l-1.3-1.4c-.7-.7-1.7-.8-2.5-.2L20 19.1l4.6 4.6 7-7.5c.6-.7.6-1.7 0-2.4z"/></g><defs><clipPath id="clip0"><path fill="#fff" transform="translate(16 11)" d="M0 0h16v16H0z"/></clipPath></defs></svg>
  </div>
</template>
<script>
export default {
  data() {
    return {
      popupInitialTopOffset: 0,
      popupInitialLeftOffset: 0,
      offsetTop: 0,
      offsetLeft: "-999em",
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

              this.offsetTop = top - this.popupInitialTopOffset - 55 + window.pageYOffset + "px";

              this.offsetLeft = left - 23 - this.popupInitialLeftOffset / 2 + "px";
            }
          }
        } else {
          this.offsetLeft = "-999em";
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
    console.log(this.$refs.popup.offsetHeight)
    this.popupInitialLeftOffset = this.$refs.popup.offsetWidth;
    window.addEventListener("mouseup", this.ListenToDocumentSelection);
  },
  destroyed() {
    window.removeEventListener("mouseup", this.ListenToDocumentSelection);
  }
};
</script>
<style scoped>
</style>
