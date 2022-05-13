<template>
  <div class="hello">

    <div class="grid grid-cols-1 lg:grid-cols-2 ">
      <div class="bg-blue-600 min-h-screen lg:flex  p-8 sm:p-12 justify-center max-h-screen" >
        <div class="lg:w-3/4 sm:h-full">
          <h1 class="text-white text-center  title">Crie seu crachá</h1>
          <p class="text-center text-blue-200 subtitle">Em poucos dias você o receberá em casa</p>
          <form action="" class="  h-16 sm:h-11  mt-8">
          <input v-model="name" placeholder="Nome" type="text" class="input w-full">
          <input v-model="tel" placeholder="Telefone" type="number" class="input w-full">
          <input v-model="Email" placeholder="Email" type="text" class="input w-full">
          <input v-model="idade" placeholder="idade" type="number" class="input w-full">          
          <div class="lg:flex lg:justify-between">
            <select v-model="sectorSelected" class="w-full lg:w-1/2 input">            
              <option v-for="sector in sectors">
                {{sector.name}}
              </option>
            </select>                  
            <label for="upload-file" class="btn btn-secondary flex align-center ">               
              <span>Escolha sua foto!</span>
              <input type="file" id="upload-file" hidden @change="uploadImage"/>
            </label>
          </div>          
        </form>    
        </div>        
      </div>

      <div class="lg:min-h-screen max-h-screen flex items-center py-5 px-12 lg:px-24 xl:px-48 xl:py-14 bg-slate-200">
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
              <p class="card-row card-mainInfo"><b>{{name}}</b></p>            
              <p v-if="!name" class="card-row card-mainInfo text-gray-500 ">{{nameDefault}}</p>
              <p class="card-row card-info"><b>Telefone: </b> {{tel}}</p>
              <p class="card-row card-info"><b>Email: </b>{{Email}}</p>
              <p class="card-row card-info"><b>Idade: </b>{{idade}}</p>              
              <p class="card-row card-info"><b>Setor: </b>{{sectorSelected}}</p>                                     
            </div>            
          </div>  
        </div>
      </div>
    </div>

    
    
  </div>
</template>

<script>
export default {
  img:'imageUpload',
  data(){
    return({
      name: '',
      nameDefault: 'Aqui ficará seu nome',
      tel: '',
      email: '',
      age: '',
      sectorSelected: '',
      
      
      previewImage: null,
      sectors: [
        {id:1,name:'Relacionamento'},
        {id:2,name:'Tecnologia'},
        {id:3,name:'Juridico'},
        {id:4,name:'Manutencao'},
      ]
    })
    
  }, 
   methods:{
            uploadImage(e){
              console.log(this.setorName);
                const image = e.target.files[0];
                const reader = new FileReader();
                reader.readAsDataURL(image);
                reader.onload = e =>{
                    this.previewImage = e.target.result;
                    console.log(this.previewImage);
                };
            },
            
            chooseFiles(){ 
              document.getElementById("fileUpload").click();
            }
        },
        
        
  props: {
    msg: String
  }
}
</script>


<style scoped> 

 </style>
