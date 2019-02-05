<template>
  <div>
    <div ref="buttonContainer" style="margin: 1rem 0;">
      <vue-bootstrap-button
        @click="click"
        :loading="loading"
        :variant="variant"
        :size="size"
        :disabled="disabled"
        text="Click me!"
      />
    </div>
    <hr/>
    <b-row>
      <b-col md="4">
        <h6>Different options</h6>
        <b-row>
          <b-col md="5" style="margin-bottom: 1rem">
            <b-radio-group
              v-model="style"
              :options="styleOptions"
              stacked
            />
          </b-col>
          <b-col md="5" style="margin-bottom: 1rem">
            <b-radio-group
              v-model="size"
              :options="sizeOptions"
              stacked
            />
            <hr style="border: 0;">
            <b-checkbox v-model="outline">Outlined</b-checkbox>
            <b-checkbox v-model="disabled">Disabled</b-checkbox>
          </b-col>
        </b-row>
      </b-col>
      <b-col md="4">
        <h6>Result code</h6>
        <pre class="example">{{ code }}</pre>
      </b-col>
    </b-row>
  </div>
</template>

<script>
  import VueBootstrapButton from '@/components/vue-bootstrap-button.vue'
  export default {
    name: 'Examples',
    components: {
      VueBootstrapButton
    },
    data () {
      return {
        loading: false,

        // button options:
        style: 'primary',
        size: 'lg',
        outline: false,
        disabled: false,

        // forms data
        styleOptions: [
          { value: 'primary', text: 'Primary' },
          { value: 'secondary', text: 'Secondary' },
          { value: 'success', text: 'Success' },
          { value: 'warning', text: 'Warning' },
          { value: 'danger', text: 'Danger' },
          { value: 'info', text: 'Info' }
        ],
        sizeOptions: [
          { value: 'lg', text: 'Large' },
          { value: '', text: 'Normal' },
          { value: 'sm', text: 'Small' }
        ]
      }
    },
    computed: {
      variant () {
        return this.outline
          ? 'outline-' + this.style
          : this.style
      },
      code () {
        return `<vue-bootstrap-button
  :variant="${this.variant}"
  :size="${this.size}"
  :disabled="${this.disabled}"
  text="Click me!"
/>`
      }
    },
    methods: {
      timeout (ms) {
        return new Promise((resolve) => setTimeout(resolve, ms))
      },
      async click () {
        this.loading = true
        await this.timeout(1000)
        this.loading = false
      }
    },
    mounted () {
      const elem = this.$refs.buttonContainer
      const rect = elem.getBoundingClientRect()
      elem.style.height = `${rect.height}px`
    }
  }
</script>

<style scoped>
  pre.example {
    margin-bottom: 1rem; 
    color: maroon; 
    font-size: 100%;
  }
</style>
