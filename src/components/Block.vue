<template>
  <div v-if="showBlock" class="block" @click="stopTimer">Click Me</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime:0
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
    }, this.delay);
    this.startTimer();
  },
  methods:{
      startTimer(){
         this.timer =  setInterval(()=>{
              this.reactionTime += 10
          },10)
      },
      stopTimer(){
          this.$emit('end',this.reactionTime)
      }
  }
};
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>