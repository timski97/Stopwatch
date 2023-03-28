<template >
  <div class="container">
    <div>
      <p>{{ formattedTime  }}</p>
    <hr class="hr-line"/>
    </div>
    <div class="button">
        <img class="button-style" @click="start()" src="../assets/start.png" alt="">
        <img class="button-style" @click="pause()" src="../assets/pause.png" alt="">
        <img class="button-style" @click="stop()" src="../assets/resert.png" alt="">
    </div>
  </div>
</template>

<script>

export default {
  name: "StopWatch",

  data() {
    return {
      timerState: 'stopped',
      currentTimer: 0,
      formattedTime: "00:00:00",
      ticker: undefined,
 

      };
  },
  
  

  methods: {
     start () {
      if (this.timerState !== 'running') {
        this.tick();
        this.timerState = 'running';
      }
    },
    pause () {
      window.clearInterval(this.ticker);
      this.timerState = 'paused';
    },
    stop () {
      window.clearInterval(this.ticker)
      this.currentTimer = 0;
      this.formattedTime = "00:00:00";
      this.timerState = "stopped";
    },
    tick () {
      this.ticker = setInterval(() => {
        this.currentTimer++;
        this.formattedTime = this.formatTime(this.currentTimer);
      }, 250)
    },
    formatTime (seconds) {
      let measuredTime = new Date(null);
      measuredTime.setSeconds(seconds);
      let MHSTime = measuredTime.toISOString().substr(11, 8);
      return MHSTime;
    }
  },
};
</script>


<style scoped>
.container {
	background-color: #696969;
	margin-bottom: 20px;
  width: 225px;
  height: 125px;
  /* padding-left: 50px; */
  margin-left: 50px;
    
}
p {
    /* padding-top: 22px; */
    color: #9E9E9E;
    font-weight: 400;
    font-size: 22px;
    line-height: 21px;
    text-align: center;
}
.button{
    flex-direction: row;
    display: flex;
    justify-content: center;
    padding-bottom: 20px;

}
.button-style{
    margin-right: 20px;
    width: 20px;
    height: 20px;
    /* display: inline-flex; */
    
}

.hr-line {
    padding: auto;
	margin: 20px 0;
	padding: 0;
	height: 0;
	border: none;
	border-top: 1px solid #9E9E9E;
}
</style>
