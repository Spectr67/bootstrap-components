<script>
import { BFormInput, BProgress } from 'bootstrap-vue-next'

export default {
  components: { BProgress, BFormInput },

  data() {
    return {
      text: '',
      lettersLimit: 10,
    }
  },
}
</script>

<template>
  <!-- input name=name input name=email -->

  <div>
    <h1>{{ text.length }}</h1>
    <BFormInput
      v-model="text"
      :maxlength="lettersLimit"
      placeholder="Enter your name"
      autocomplete="none"
      spellcheck="false"
    />
    <BProgress
      variant="success"
      height="3px"
      :max="lettersLimit"
      :value="text.length"
    />
  </div>
</template>
