<template>
  <div class="wrapper">
    <h1 id="title">Countdown to Paradise</h1>
    <div class="countdown-wrapper">
      <span class="number">
        {{days}}
        <span class="title">Days</span>
      </span>
      <span class="number">
        {{hours}}
        <span class="title">Hours</span>
      </span>
      <span class="number">
        {{mins}}
        <span class="title">Minutes</span>
      </span>
      <span class="number">
        {{secs}}
        <span class="title">Seconds</span>
      </span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return{
      target: new Date(),
      time: 0,
    }
  },
  created(){
    this.target = new Date(2023, 8, 26, 0, 0, 0, 0);

    setInterval(() => {
      this.time = this.target.getTime() - new Date().getTime();
    }, 1000)
  },
  computed: {
    days(){
      const d = Math.floor(this.time / (24 * 3600 * 1000));
      return `${d}`;
    },
    hours()
    {
      let t = this.time;
      const d = Math.floor(t / (24 * 3600 * 1000));
      t = t - (d * 24 * 3600 * 1000);
      const h = Math.floor(t / (3600 * 1000));
      return h;
    },
    mins(){
      let t = this.time;
      const d = Math.floor(t / (24 * 3600 * 1000));
      t = t - (d * 24 * 3600 * 1000);
      const h = Math.floor(t / (3600 * 1000));
      t = t - (h * 3600 * 1000);
      const m = Math.floor(t / (60 * 1000));
      return m;
    },
    secs(){
      let t = this.time;
      const d = Math.floor(t / (24 * 3600 * 1000));
      t = t - (d * 24 * 3600 * 1000);
      const h = Math.floor(t / (3600 * 1000));
      t = t - (h * 3600 * 1000);
      const m = Math.floor(t / (60 * 1000));
      t = t - (m * 60 * 1000);
      const s = Math.floor(t / (1000));
      return s;
    },
  }
}
</script>

<style>
html{
  width: 100vw;
  height: -webkit-fill-available;
  margin: 0;
  padding: 0;
}

body{
  width: 100vw;
  min-height: 100vh;
  min-height: -webkit-fill-available;
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  width: 100vw;
  height: 100vh;

  background-image: url("./assets/IMG_5567.JPG");
  background-position: center;
  background-size: contain;
  background-repeat: no-repeat;
  background-color: #A0C49D;
}

#title{
  position: absolute;
  top: 0.5em;
  left: 0; right: 0;
  font-size: 3vw;
  margin: 0;
  color: #17594A;
}

.countdown-wrapper{
  position: absolute;
  bottom: 1em;
  left: 0; right: 0;
  margin: auto;
  font-size: 28pt;
  background-color: rgba(255, 255, 255, 0.95);
  width: fit-content;
  color: #85A389;
  border-radius: 10px;
  box-shadow: 0 0 2px 1px #85A389;
}

.number{
  /* border: 1px solid black; */
  width: min-content;
  font-size: 5vw;
  margin: 0.25em;
}

.number .title{
  font-size: 0.5em;
}
</style>
