<template>  
<Sucess v-if="sucess"/>
  <div id="card" class="card ">
    <div class="flex justify-center relative">
      <img v-if="!previewImage" class="avatar" src="../assets/avatar.png" alt=""/> 
      <img :src="previewImage" class="avatar" />
      <img class="card-icon" v-if="sectorSelected == 'Relacionamento'" src="../assets/headset.png" alt="Ícone de Headset"/>
      <img class="card-icon" v-if="sectorSelected == 'Tecnologia'" src="../assets/coding.png" alt="Ícone de computador"/>
      <img class="card-icon" v-if="sectorSelected == 'Jurídico'" src="../assets/balance.png" alt="ícone de balança"/>
      <img class="card-icon" v-if="sectorSelected == 'Manutenção'" src="../assets/mechanic.png" alt="Ícone de ferramentas"/>     
    </div>
    
    <div class="sm:flex sm:items-center"> 
      <div class="text-sm">        
        <p class="card-row card-mainInfo card-item__focus"><b>{{name}}</b></p>        
        <p v-if="!name" class="card-row card-mainInfo text-gray-500 ">{{nameDefault}}</p>
        <p id="" class="card-row card-info"><b>Telefone: </b> {{tel}}</p>
        <p class="card-row card-info"><b>Email: </b>{{email}}</p>
        <p class="card-row card-info"><b>Idade: </b>{{age}}</p>              
        <p class="card-row card-info"><b>Setor: </b>{{sectorSelected}}</p>                                     
      </div>            
    </div>  
  </div>      
</template>

<script>
import Sucess from './Sucess.vue'

export default {
  img:'imageUpload',
  components:{
    Sucess
  },
  data(){
    return({      
      nameDefault: 'Aqui ficará seu nome',                 
    })
    
  }, 
                   
  props: {
    name: String,
    tel: String,
    email: String,
    age: String,
    sectorSelected: String,
    previewImage: String,
    sucess: Boolean
  }
}
</script>


<style scoped> 

 </style>
