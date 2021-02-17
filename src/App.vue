<template>
  <div class="m_homePage" >
    <div class="m_getButton" @click="fetchData">
      Fetch Data
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  methods:{
    fetchData(){

      axios.get('https://jsonplaceholder.typicode.com/posts')
      .then((results)=>{

        const newResult = results.data.map(result =>{
          //check if id us even
          if(result.id % 2 == 0){
            //If id even then convert to upperCase and return the updated object to the new array
            result.title = result.title.toUpperCase()
            return result;
          }else{
            return result;
          }
        });
        console.log(newResult);//Log all the updated results
      })
      .catch((err)=>{
        console.log(err);
      })
    }
  }
}
</script>

<style scoped>
  .m_homePage{
    display: flex;
  }

  .m_getButton{
    cursor: pointer;
    border: 1px solid black;
    border-radius: 35px;
    
    padding: 6px;
    display: flex;
    margin: 20px auto;
  }

  .m_getButton:hover{
    background: blue;
    color: white;
  }
</style>