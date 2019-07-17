<template>
  <div id="dsl" class="column">
    <file-reader @load="parse_ds($event)"></file-reader>
    <textarea class="textarea" placeholder="10 lines of textarea" rows="10" v-model="text"></textarea>
    <div>
        The content of the file is <span v-if="valid"> OK!!  </span>

        <table class="table">
            <thead>
                <tr>
                    <th>Property</th>
                    <th>Value</th>
                </tr>
            </thead>
            <tbody>
            <tr>
                <th>Number of columns</th>
                <td>{{ ds_cols }}</td>
            </tr>
            <tr>
                <td>Number of rows</td>
                <td>{{ ds_rows }}</td>
            </tr>
            </tbody>
        </table>
    </div>
</div>
</template>

<script>
  import FileReader from './DatasetLoader/FileReader'

  export default {
    name: 'dataset-loader',
    data: () => ({
      text: '',
      valid: true,
      dataset: {}
    }),
    components: {FileReader},
    methods: {
      parse_ds (text) {
        this.text = text
        this.valid = true
        try {
          this.dataset = JSON.parse(text)
        } catch (e) {
          this.valid = false
        }
      }
    }
  }
</script>

<style>

</style>
