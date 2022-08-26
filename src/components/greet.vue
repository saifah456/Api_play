<template>
<div>
    
    Hello My name is :{{name}} {{lname}}

    <button @click="callApi">API</button>
    Api Data: 
    {{apiData}} 
    

</div>


</template>
<script>

 import axios from 'axios'

 
export default {
  name: 'greetNow',

  props:{
    name:String,
    lname:String
  },
   
   data(){
        return{
            apiData : "",
        }
   },
  methods: {
     callApi(){
        axios.get('https://jsonplaceholder.typicode.com/posts/1')
        .then(  // on resolve
            (api_data)=>{
                console.log("API Data" ,api_data.data)
                this.apiData=api_data.data

            }
        )
        .catch(  // on error/ reject
            function rem(error){
                console.log("API Error",error)
            }
        )
     }
  },
  
}
</script>

