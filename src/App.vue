<template>
  <div class="flex justify-center">
    <div class="flex justify-center flex-col w-6/12">
      <span class="m-8"></span>
      <h1 class="text-center text-lg font-mono font-bold text-2xl">Is that a cake? Upload your image!</h1>
      <div class="flex justify-center">
        <input type="file" @change="onFileChange">      
      </div>
      <div v-if="url"  class="m-8 flex justify-center flex-col">
        <img :src="url" class="object-center">
        <p class="text-center" :class="{yes: finished}">{{result}}</p>
      </div>
    </div>
  </div>  
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      url: null,
      result: "...processing",
      finished: false,
    }
  },
  methods: {
    onFileChange(e) {
      const file = e.target.files[0];
      this.url = URL.createObjectURL(file);
      this.result = "...processing";
      this.finished = false;
      setTimeout(()=>{
        this.result="YES";
        this.finished = true;
        }, 2000);
    }
  }
}
</script>

<style>
  #image-box {
    width: 50%;
  }

  .yes {
    color: #42b883;
    font-weight: bolder;
    font-size: 5em;
  }
</style>
