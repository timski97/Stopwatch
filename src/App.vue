 <template>
      <div class="container-wrap">
        <Stopwatch v-for="field in fields" 
          :id="field.id" 
          :key="field.id"  
          ref="fieldRefs" />
        <button @click="addTimer()"  class="container-add">
          <img class="button-add"  src="./assets/plus.png" alt="">
        </button>
    </div>
 </template>

 <script setup >

import { ref } from 'vue'
import Stopwatch from './components/Stopwatch.vue'
 let timerCount = 0
 const fields = ref([
	{id: 0}
])
 const fieldRefs = ref([])
 function addTimer() {
	console.log(1)
	timerCount++
	fields.value.push({
		id: timerCount++
	})
  
}
 </script>
 <script>
 export default{
   name: "App",
   components:{

      Stopwatch,
   },
  
}
 </script>
 
<style scoped>
 @media (min-width: 768px)  { 
  .container-wrap{
    width: 824px;
  }
  }
@media (min-width: 1024px) { 
  .container-wrap{
    width: 1099px;

  }
 }

.container-wrap{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }
  .container-add {
    border: 0;
    display: flex;
    margin-left: 50px;
    justify-content: center;
    align-items: center;
    width: 225px;
    height: 125px;
    margin-bottom: 20px;
    background-color:#696969 ;

}
  .button-add{
    width: 20px;
    height: 20px;
}
</style>