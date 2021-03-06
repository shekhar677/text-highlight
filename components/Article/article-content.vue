<template>
  <div class="flex items-center justify-center min-h-screen bg-bg-gray">
    <div class="w-11/12 md:w-8/12 lg:w-7/12 mx-auto bg-white shadow md:mx-24 my-6 md:my-16 rounded-md">
      <div class="p-6 md:p-16" ref="content" id="content">
        <h1 class="font-bold text-3xl md:text-4xl mb-2">I was wrong about macOS Big Sur...</h1>
        <p class="my-4">A month ago, I published my story about macOS Big Sur review. I wrote about how macOS Big Sur has a big design overhaul, however with a performance bummer. Last time when I reviewed it, my early-2020 Base Model MacBook Pro had a significant performance decrease in speed and battery life, which made me unhappy with the update. Take note that this was the first public release of macOS Big Sur.</p>
        <p class="my-4">Not long ago after I published that story, Apple released a new update for Big Sur, which is 11.1. I also received some feedback from the Medium community here saying that I used too much non-Apple application, which has a significant hit on performance and battery (in particular, Google Chrome).</p>
        <p class="my-4">That’s why, I decided to have a little experiment, which is to go full-on Safari. I also decided to not charge my MacBook Pro not often and see how much it lasts for a single charge.</p>
        <p class="my-4">The result was surprising to me and I have to admit that I ate up my own words on my previous story. It is crazy how heavy the impact is from a third-party application. Well, Chrome is definitely a fast browser, but also fast in draining my MacBook’s battery.</p>
        <p class="my-4">My experience with Safari is very smooth, as I don’t need to worry about plugging my MacBook oftenly. Checking emails, social media, watching YouTube and writing stories in Medium did not affect my battery significantly. Plus, I also get better security with Safari with its latest tracking prevention update.</p>
        <p class="my-4">Last time when I use Safari in Catalina, YouTube only capable of showing 1080p videos at its max resolution. Now, the new update allows Safari to view up to 4k HDR content, which makes me happier. It means that I can continue using Safari to watch high-quality videos.</p>
      </div>
      <hightlight />
    </div>
  </div>
</template>

<script>
import Hightlight from '~/components/TextHighlight/hightlight';

export default {
  components: {
    Hightlight
  },
  data() {
    return {
      // text: undefined
    }
  },
  methods: {
    // selection() {
    //   const selectedData = window.getSelection();
    //   if (selectedData && !selectedData.isCollapsed) {
    //     this.text = selectedData.toString();
    //     console.log('sel: ', this.text)
    //   }
    // }
  },
  // mounted() {
  //   if (process.client) {
  //     window.addEventListener('mouseup', this.selection);
  //   }
  // },
  // beforeDestroy() {
  //   window.removeEventListener('mouseup', this.selection)
  // }
}
</script>

<style>

</style>