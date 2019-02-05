# vue-bootstrap-button

A button component with “loading” and “done” indicators.

After you click the button it transforms into endless loading progress. When response comes, okay sign appears and button returns to its normal state.

## Features
- Vue 2 using Bootstrap 4 compatible.
- Easy to use.
- Material design icons in box.

## Getting started
### Installation
```
$ npm install vue-bootstrap-button --save
```

### How to use
Simply import component and use it on the page. Set loading property to true when data loading starts and to false after finish.
```
<template>
  <!-- Form here -->
  <vue-bootstrap-button
    text="Submit"
    :loading="loading"
    @click="submit"
  />
</template>
<script>
  import VueBootstrapButton from 'vue-bootstrap-button'

  export default {
    data () {
      return {
        loading: false;
      }
    },
    methods: {
      submit () {
        this.loading = true
        // Await data posting and response here
        this.loading = false
      }
    }
  }
</script>
```
