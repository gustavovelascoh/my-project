<template>
  <div id="wrapper">
    <img id="logo" src="~@/assets/logo.png" alt="electron-vue">
    <div class="title"> EXAMPLE APP USING ELECTRON+VUE+D3.JS </div>
    <div class="subtitle"> Self monitor app </div>
    <div class="columns">
      <div class="column is-one-quarter">
        <system-information></system-information>
        <self-monitor-summary></self-monitor-summary>
      </div>
        <dataset-loader></dataset-loader>
    </div>
  </div>
</template>

<script>
  import SystemInformation from './LandingPage/SystemInformation'
  import DatasetLoader from './LandingPage/DatasetLoader'
  import SelfMonitorSummary from './LandingPage/SelfMonitor/SelfMonitorSummary'

  export default {
    name: 'landing-page',
    components: {
      SystemInformation,
      DatasetLoader,
      SelfMonitorSummary
    },
    methods: {
      open (link) {
        this.$electron.shell.openExternal(link)
      }
    }
  }
</script>

<style>
  @import url('https://fonts.googleapis.com/css?family=Source+Sans+Pro');

  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body { font-family: 'Source Sans Pro', sans-serif; }

  #wrapper {
    background:
      radial-gradient(
        ellipse at top left,
        rgba(255, 255, 255, 1) 40%,
        rgba(229, 229, 229, .9) 100%
      );
    height: 100vh;
    padding: 30px 40px;
    width: 100vw;
  }

  #logo {
    height: auto;
    margin-bottom: 20px;
    width: 420px;
  }

  main {
    display: flex;
    justify-content: space-between;
  }

  main > div { flex-basis: 50%; }

  .left-side {
    display: flex;
    flex-direction: column;
  }

  .welcome {
    color: #555;
    font-size: 23px;
    margin-bottom: 10px;
  }

  .title {
    color: #2c3e50;
    font-size: 20px;
    font-weight: bold;
    margin-bottom: 6px;
  }

  .title.alt {
    font-size: 18px;
    margin-bottom: 10px;
  }

  .doc p {
    color: black;
    margin-bottom: 10px;
  }

  .doc button {
    font-size: .8em;
    cursor: pointer;
    outline: none;
    padding: 0.75em 2em;
    border-radius: 2em;
    display: inline-block;
    color: #fff;
    background-color: #4fc08d;
    transition: all 0.15s ease;
    box-sizing: border-box;
    border: 1px solid #4fc08d;
  }

  .doc button.alt {
    color: #42b983;
    background-color: transparent;
  }
</style>
