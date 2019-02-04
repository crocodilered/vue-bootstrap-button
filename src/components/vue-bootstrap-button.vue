<template>
  <b-button
    ref="button"
    :variant="variant"
    :size="size"
    :class="{ 'material-icons': state !== 1}"
    :pressed="state !== 1"
    @click.prevent="click"
  >
    <span v-show="state === 1">{{ label }}</span>
    <span v-show="state === 2" class="rotating">refresh</span>
    <span v-show="state === 3">check</span>
  </b-button>
</template>

<script>
  import 'material-icons/iconfont/material-icons.css'

  const data = function () {
    return {
      // State of the button:
      //   norm - 1
      //   loading start - 2
      //   loading finish - 3
      state: 1
    }
  }

  const watch = {
    loading: {
      handler (val) {
        if ( val ) {
          this.state = 2
        } else {
          this.state = 3
          setTimeout(() => (this.state = 1), 1000)
        }
      }
    } 
  }

  const methods = {
    click () {
      if (this.state === 1) {
        this.$emit('click')
      }
    }
  }

  export default {
    name: 'Button',
    props: ['loading', 'variant', 'size', 'label'],
    data,
    watch,
    methods,
    mounted () {
      // To prevent button resizing while changing content
      const buttonRect = this.$refs.button.getBoundingClientRect()
      this.$refs.button.style.width = `${buttonRect.width}px`
    }
  }
</script>

<style>
  button {
    overflow: hidden;
  }
  .rotating {
    display: inline-block;
    -webkit-animation: spin 1s linear infinite;
    -moz-animation: spin 1s linear infinite;
    animation: spin 1s linear infinite;
  }
  @-moz-keyframes spin {
    100% { -moz-transform: rotate(360deg); }
  }
  @-webkit-keyframes spin {
    100% { -webkit-transform: rotate(360deg); }
  }
  @keyframes spin {
    100% { -webkit-transform: rotate(360deg); transform:rotate(360deg); }
  }
</style>
