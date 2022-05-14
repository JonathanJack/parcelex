<template>  
  <div class="card">
    <div class="flex justify-center relative">
      <img v-if="!previewImage" class="avatar" src="../assets/avatar.png"/> 
      <img :src="previewImage" class="avatar" />
      <img class="card-icon" v-if="sectorSelected == 'Relacionamento'" src="../assets/headset.png"/>
      <img class="card-icon" v-if="sectorSelected == 'Tecnologia'" src="../assets/coding.png"/>
      <img class="card-icon" v-if="sectorSelected == 'Juridico'" src="../assets/balance.png"/>
      <img class="card-icon" v-if="sectorSelected == 'Manutencao'" src="../assets/mechanic.png"/>     
    </div>
    
    <div class="sm:flex sm:items-center"> 
      <div class="text-sm">
        <transition name="slide-fade-up">
          <p class="card-row card-mainInfo teste"><b>{{name}}</b></p>
        </transition>            
        <p v-if="!name" class="card-row card-mainInfo text-gray-500 ">{{nameDefault}}</p>
        <p class="card-row card-info"><b>Telefone: </b> {{tel}}</p>
        <p class="card-row card-info"><b>Email: </b>{{Email}}</p>
        <p class="card-row card-info"><b>Idade: </b>{{idade}}</p>              
        <p class="card-row card-info"><b>Setor: </b>{{sectorSelected}}</p>                                     
      </div>            
    </div>  
  </div>      
</template>

<script>
export default {
  img:'imageUpload',
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
    previewImage: String
  }
}
</script>


<style scoped> 

 </style>
