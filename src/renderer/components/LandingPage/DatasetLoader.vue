<template>
  <div id="dsl" class="column">
    <file-reader @load="text = $event"></file-reader>
    <textarea class="textarea" placeholder="10 lines of textarea" rows="10" v-model="text"></textarea>
</div>
</template>

<script>
  import FileReader from './DatasetLoader/FileReader'

  export default {
    name: 'dataset-loader',
    data: () => ({ text: '' }),
    components: {FileReader}
  }
</script>

<style>

</style>
