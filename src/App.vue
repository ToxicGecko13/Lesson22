<template>
  <div id="app">
    <img alt="Active Martial Arts Logo" src="./assets/ActiveLogo.png">
    <button v-on:click="showAll">Show All</button>
    <ul class="AwardsList">
      <award-card 
        v-for="award in awards" 
        v-bind:key="award.id" 
        v-bind:award="award" 
        v-on:hide="hideCard($event)"
        v-show="award.show"/>
    </ul>
  </div>
</template>

<script>
import AwardCard from './components/AwardCard.vue'

export default {
  name: 'app',
  components: {
    AwardCard
  },
  methods: {
    hideCard: function(id) {
      //alert(id);
      let award = this.awards.filter(award => award.id === id)[0];
      award.show = false;
      alert(JSON.stringify(award));
    },
    showAll: function() {
      this.awards.forEach(award => {
        award.show = true;
      });
    },
  },
  data () {
    return {
      awards: [
        {
          id: 1,
          title: 'High Kick',
          detail: 'Kick over your head 10 times in under 10 seconds.',
          imageurl: require('./assets/clouds-fight-jumping-62376.jpg'),
          show: true
        },
        {
          id: 2,
          title: 'Closed Fist',
          detail: 'Break a 1 inch wood board with closed fist.',
          imageurl: require('./assets/aggressive-anger-angry-163431.jpg'),
          show: true
        },
        {
          id: 3,
          title: 'Dragon Spirit',
          detail: 'Complete Your Form 100 Times',
          imageurl: require('./assets/bokeh-daylight-dragon-208326.jpg'),
          show: true
        },
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background: linear-gradient(
    rgba(200, 200, 200, 0.6),
    rgba(80, 80, 80, 0.7)
  )
}

.AwardsList {
  list-style-type: none;
}
</style>
