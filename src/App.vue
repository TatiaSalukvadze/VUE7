<template>
  <h1>way 1: Seperate refs:</h1>
  <h2>My Course Goal</h2>
  <!-- Task 1: Output your main course goal with help of the composition API -->
  <!-- Don't hardcode it into the template, instead hardcode it into the JS code -->
  <h3 v-if="show">{{myGoal}}</h3>
  <!-- Task 2: Toggle (show/ hide) the goal with help of the button  -->
  <h1>Way 2: Ref object:</h1>
  <h2>My Course Goal</h2>
  <h3 v-if="refObj.show">{{refObj.goal}}</h3>

  <h1>Way 3: Reactive object:</h1>
  <h2>My Course Goal</h2>
  <h3 v-if="reactObj.show">{{reactObj.goal}}</h3>

  <button @click="setShow">Toggle Goal</button>
  <!-- Task 3: Manage data in three ways -->
  <!-- => Separate refs -->
  <!-- => Ref Object -->
  <!-- => Reactive Object -->

  <!-- Task 4: Also solve the assignment with the Options API -->
  <h1>Way 4: Now Using Options API:</h1>
  <h2>My Course Goal</h2>
  <h3 v-if="showOAPI">{{goalOAPI}}</h3>

  <button @click="setShowOAPI">Toggle Goal</button>
  
</template>

<script>//alternative <script setup> and import da setup-is codi darcheba marto, export da setup() agar
import {ref, reactive} from 'vue';

export default {
  setup(){
    //way 1: Seperate refs
    const goal = ref("Improvement, Knowledge, Experience!");
    const show = ref(true);

    //Way 2: Ref object
    const refObj = ref({goal: "Improvement, Knowledge, Experience!", show:true});

    //Way 3: Reactive object
    const reactObj = reactive({goal: "Improvement, Knowledge, Experience!", show:true});

    function setShow(){
      show.value = !show.value;//way 1: Seperate refs
      refObj.value.show = !refObj.value.show;//Way 2: Ref object
      reactObj.show = !reactObj.show;//Way 3: Reactive object
    }

    

    return {myGoal: goal, show: show, refObj: refObj, reactObj: reactObj, setShow:setShow};
  },

  data(){
    return{
      goalOAPI:"Improvement, Knowledge, Experience!",
      showOAPI: true
    }
  },
  methods:{
    setShowOAPI(){
      this.showOAPI = !this.showOAPI;
    }
  }
 
}

//ref-isas setupshi shecvlistvis goal.value = * unda daiweros
//reactive objectebtanaa da .value ar unda, reactive ari object da ara shignit cvladebi,toRefs shegvidzia use
</script>

<style>
html {
  font-family: sans-serif;
}
body {
  margin: 3rem;
  text-align: center;
}
</style>