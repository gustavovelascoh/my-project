<template>
    <div class="file has-name is-fullwidth">
    <label class="file-label">
      <input class="file-input" type="file" name="resume" @change="loadTextFromFile">
      <span class="file-cta">
        <span class="file-icon">
          <i class="fas fa-upload"></i>
        </span>
        <span class="file-label">
          Choose a file…
        </span>
      </span>
      <span class="file-name">
        .csv file
      </span>
    </label>
  </div>
</template>

<script>
export default {
  methods: {
    loadTextFromFile (ev) {
      const file = ev.target.files[0]
      const reader = new FileReader()
      reader.onload = e => this.$emit('load', e.target.result)
      reader.readAsText(file)
    }
  }
}
</script>

<style>

</style>
