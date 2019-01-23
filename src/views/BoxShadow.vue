<template>
  <div>
    <h1>
      box-shadow
    </h1>
    {{log(boxShadowStyle)}}
    <!-- <div class="box-shadow" :style="boxShadowStyle"></div> -->
    <div class="box-shadow" :style="boxShadowStyle"></div>
    <Progress label="offset x" :min="-100" :max="100" :onChange="change(0)"/>
    <Progress label="offset y"  :min="-100" :max="100" :onChange="change(1)"/>
    <Progress label="blur radius"   :onChange="change(2)"/>
    <Progress label="spread radius"  :min="-100" :max="100" :onChange="change(3)"/>
  </div>
</template>

<script>
import Progress from '@/squid/Progress'
  export default {
    data: ()=>({
      boxShadow: [
        0, // offset x
        0, // offset y
        0, // blur radius
        0, // spread redius
      ]
    }),
    components: {
      Progress,
    },
    computed: {
      boxShadowStyle() {
       return {
         boxShadow: this.boxShadow.join('px ') + 'px #000'
       }
      }
    },
    methods: {
      change(index) {
        return (val) => {
          this.$set(this.boxShadow, index, val)
        }
      },
      log(...arg) {
        console.log(...arg)
      }
    }
  }
</script>

<style scoped>
  .box-shadow {
    width: 250px;
    height: 250px;
    background-color: #e1e1e1;
    margin: 100px;
  }
</style>
