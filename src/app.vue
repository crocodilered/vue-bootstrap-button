<template>
  <div id="app">
    <b-navbar toggleable="md" type="dark" variant="info">
      <b-navbar-brand>vue-bootstrap-button</b-navbar-brand>
    </b-navbar>
    <b-container style="margin-top: 1em;">
      <h1 class="main">
        <b>A button component</b><br/>
        with “loading” and “done” indicators.
      </h1>

      <h2 id="features">Features</h2>
      <ul class="features">
        <li>Vue 2 using Bootstrap 4 compatible.</li>
        <li>Easy to use.</li>
        <li>Material design icons in box.</li>
      </ul>

      <h2 id="installation">Installation</h2>
      <pre>$ npm install vue-bootstrap-button --save</pre>

      <h2 id="examples">Examples</h2>
      <examples/>

      <!--h2>Customising icons</h2>
      <p>See <a href="https://material.io/tools/icons/">material design icons</a>.</p-->

      <h2 id="reference">Reference</h2>
      <table class="reference">
        <tr>
          <th colspan="3">Properties</th>
        </tr>
        <tr>
          <td><code>text</code></td>
          <td><code>String</code></td>
          <td>Button label</td>
        </tr>
        <tr>
          <td><code>variant</code></td>
          <td><code>String</code></td>
          <td>Button style<br/>Read <a href="https://bootstrap-vue.js.org/docs/components/button/#button-contextual-variants">"Button contextual variants" section</a> on BV-site.</td>
        </tr>
        <tr>
          <td><code>size</code></td>
          <td><code>String</code></td>
          <td>Button size<br/>Read <a href="https://bootstrap-vue.js.org/docs/components/button/#button-sizing">"Button sizing" section</a> on BV-site.</td>
        </tr>
        <tr>
          <td><code>disabled</code></td>
          <td><code>Boolean</code></td>
          <td>Button disabled state.</td>
          <td/>
        </tr>
        <tr>
          <th colspan="3">Events</th>
        </tr>
        <tr>
          <td colspan="2"><code>click</code></td>
          <td>Button clicked.</td>
        </tr>
      </table>
    </b-container>
  </div>
</template>

<script>
  
  import Examples from './components/examples.vue'

  export default {
    name: 'App',
    components: {
      Examples
    }
  }
</script>

<style>
  #app {
    margin-bottom: 2rem;
  }

  h2 {
    margin: 2rem 0 1rem!important;
  }

  h1.main {
    margin: 4rem 0;
  }

  h1.main b {
    font-weight: 500;
  }

  ul.features li {
    font-size: 120%;
  }

  table.reference th {
    font-weight: 500;
    border-bottom: 1px solid #ddd;
    padding: 1.5rem 2rem .5rem 0;
  }

  table.reference tr:first-child th {
    padding-top: 0rem;
  }

  table.reference td {
    padding: .5rem 2rem .5rem 0;
    vertical-align: top;
    border-bottom: 1px solid #ddd;
  }

  table.reference td:last-child {
    padding-right: 0;
  }

  table.reference code {
    color: maroon;
    font-size: 100%;
  }
</style>
