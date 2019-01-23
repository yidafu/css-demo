<template>
  <div class="progress">
    <span>{{label}}</span>
    <div class="container" @click="handleClick">
      <div :style="line" class="line"></div>
    </div>
  </div>
</template>

<script>
const DEFAULT_WIDTH = 500

  export default {
    data: () => ({
      line: {
        width: '0px',
      },
    }),
    props: {
      label: String,
      onChange: Function,
      min: {
        type: Number,
        default: 0
      },
      max: {
        type: Number,
        default: 100
      },
    },
    methods: {
      handleClick (e) {
        const offset = e.offsetX
        this.line.width = offset + 'px';
        const offsetVal = this.getOffset(offset)
        this.onChange && this.onChange(offsetVal)
      },
      getOffset(num) {
        return (this.min + (this.max - this.min) / DEFAULT_WIDTH * num).toFixed(2)
      }
    }
  }

</script>

<style lang="scss" scoped>
   .progress {
    height: 1em;
    margin: 0.5em 0;
    span {
      padding: 0 1em;
    }
    .container,.line {
      border-radius: 5px;
      padding: 0;
      height: 10px;
    }

    .container {
      width: 500px;
      background: #f5f5f5;
      display: inline-block;
      .line {
        width: 0px;
        background-color: #1890ff;
      }
    }
  }

</style>
