<template>
  <div class="preview">
    <ul>
      <li v-for="(gif, index) in gifs" :key="index">
        <img :src="gif.images.fixed_height.url" :alt="index" />
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  props: ["gifs"]
};
</script>
<style>
ul li{
    list-style-type: none;
    float: left;
    margin: 20px;
}
</style>