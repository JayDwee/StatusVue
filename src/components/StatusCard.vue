<template>
  <div class="status-div">
    <div class="title">
      <h1>{{ title }}</h1>
    </div>
    <div class="status status-up" v-if="status==200">
    <!-- <gg-icon class="gg-check"></gg-icon> -->
      <div class="gg-check status-icon"></div>
    </div>
    <div class="status status-down" v-else-if="status != undefined">
      <div class="gg-close status-icon"></div>
    </div>
    <div class="status status-unknown" v-else>
      <div class="gg-timer status-icon"></div>
    </div>
    </div>
</template>

<script lang="ts">
import axios  from 'axios';
import { Options, Vue } from 'vue-class-component';

@Options({
  props: {
    title: String,
    url: String
  }
})
export default class StatusCard extends Vue {
  title!: string
  url!: string
  status?: number
  data() {
    return {
      status: undefined
    }
  }

  async mounted() {
    try {
      console.log("status=",this.status)
      let result = await axios.get(this.url)
      this.status = result.status
    } catch {
      this.status = 0
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.status-div {
  width: 252px;
  height: 265px;
  background: #F7ECE1;
  border-radius: 30px;
  box-shadow: 15px 15px 30px #bebebe,
             -15px -15px 30px #ffffff;
  transition: 0.2s ease-in-out;
  margin: 2%;
}

.title {
  background-color: #F7ECE1;
  border-top-left-radius: 30px;
  border-top-right-radius: 30px;
}

.status {
  width: 100%;
  height: 80%;
  border-bottom-left-radius: 30px;
  border-bottom-right-radius: 30px;
  align-items: center;
  text-size-adjust: inherit;
  display: flex;
  /* align-items: top; */
  /* justify-content: right; */
}

.status-icon {
  object-fit: contain; 
  /* display: flex; */
  width:fit-content; 
  height: fit-content; 
  align-items: center;
  justify-content: center;
  --ggs: 5;
}

.status-up {
  background-color: #6D9F71;
}

.status-down {
  background-color: #FF6663;
}

.status-unknown {
  background-color: #aeaeae;
}

h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
