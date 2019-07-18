<template>
  <div>
    <div class="title">Information (Refresh time: {{ timestep }} ms)</div>
    <div class="items">
      <div class="item">
        <div class="name">Uptime:</div>
        <div class="value">{{ uptime }} seconds</div>
      </div>
      <div class="item">
        <div class="name">CPU Usage:</div>
        <div class="value">{{ cpuUsage }}</div>
      </div>
      <div class="item">
        <div class="name">Memory Usage:</div>
        <div class="value">{{ memUsage }}</div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data () {
      var status = {
        uptime: this.timeToHMS(process.uptime()),
        cpuUsage: process.getCPUUsage(),
        memUsage: process.memoryUsage(),
        timestep: 1000
      }
      return status
    },
    created () {
      this.timer = setInterval(this.updateVars, this.timestep)
    },
    methods: {
      updateVars: function () {
        this.uptime = this.timeToHMS(process.uptime())
        this.cpuUsage = process.getCPUUsage()
        this.memUsage = process.memoryUsage()
      },
      timeToHMS: function (seconds) {
        var hours = Math.floor(seconds / 3600)
        var minutes = Math.floor((seconds - (hours * 3600)) / 60)
        seconds = seconds - (hours * 3600) - (minutes * 60)

        // round seconds
        seconds = Math.round(seconds * 100) / 100

        var result = (hours < 10 ? '0' + hours : hours)
        result += ':' + (minutes < 10 ? '0' + minutes : minutes)
        result += ':' + (seconds < 10 ? '0' + seconds : seconds)
        return result
      }
    }
  }
</script>

<style scoped>
  .title {
    color: #888;
    font-size: 18px;
    font-weight: initial;
    letter-spacing: .25px;
    margin-top: 10px;
  }

  .items { margin-top: 8px; }

  .item {
    display: flex;
    margin-bottom: 6px;
  }

  .item .name {
    color: #6a6a6a;
    margin-right: 6px;
  }

  .item .value {
    color: #35495e;
    font-weight: bold;
  }
</style>
