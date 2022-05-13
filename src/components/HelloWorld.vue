<template>
  <div class="hello">

    <div class="grid grid-cols-1 lg:grid-cols-2 ">
      <div class="bg-blue-600 min-h-screen lg:flex  p-8 sm:p-12 justify-center max-h-screen" >
        <div class="lg:w-3/4 sm:h-full">
          <h1 class="text-white text-center  text-5xl lg:text-5xl mb-2">Crie seu crachá</h1>
          <p class="text-center text-blue-200 text-2xl sm:text-lg">Em poucos dias você o receberá em casa</p>

          <form action="" class="  h-16 sm:h-11  mt-8">
          <input v-model="name" placeholder="Nome" type="text" class="flex-1 h-16 sm:h-11 w-full my-8 sm:my-4 text-center text-gray-700 bg-gray-200 rounded-md hover:bg-hite border border-gray-200 outline-none">
          <input v-model="tel" placeholder="Telefone" type="number" class="flex-1 h-16 sm:h-11 w-full text-center my-8 sm:my-4 text-gray-700 bg-gray-200 rounded-md hover:bg-hite border border-gray-200 outline-none">
          <input v-model="Email" placeholder="Email" type="text" class="flex-1 h-16 sm:h-11 w-full my-8 sm:my-4 text-center text-gray-700 bg-gray-200 rounded-md hover:bg-hite border border-gray-200 outline-none">
          <input v-model="idade" placeholder="idade" type="number" class="flex-1 h-16 sm:h-11 w-full my-8 sm:my-4 text-center text-gray-700 bg-gray-200 rounded-md hover:bg-hite border border-gray-200 outline-none">          
          <div class="lg:flex lg:justify-between">
            <select v-model="sectorSelected" class="sm:w-screen lg:w-1/2 h-13 h-16 sm:h-11 my-8 sm:my-4 text-gray-700 bg-gray-200 rounded-md hover:bg-hite border border-gray-200 outline-none">            
              <option v-for="sector in sectors">
                {{sector.name}}
              </option>
            </select>          
          

              <label for="upload-file" class="h-16  sm:h-11  sm:my-4 flex align-center text-gray-200 bg-red-500 hover:text-red-500 hover:bg-gray-200 border-red-500 
              font-semibold rounded-md text-xs px-4 ">
                <span>Escolha sua foto!</span>
                <input type="file" id="upload-file" hidden @change="uploadImage"/>
              </label>
          </div>

          
        </form>
    
        </div>        
      </div>

      <div class="lg:min-h-screen max-h-screen flex items-center py-5 px-12 lg:px-24 xl:px-48 xl:py-14 bg-slate-200">

        <div class=" bg-white shadow-xl rounded-lg border border-gray-300 px-14 py-3 items-center text-center w-80 ">
          <div class="flex justify-center">
           <img v-if="!previewImage" class="h-1/3" src="../assets/avatar.png"/> 
           <img :src="previewImage" class="uploading-image sm:flex-shrink-0 mx-auto sm:mx-0 h-1/3 rounded-full" />
          </div>
          
          <div class="sm:flex sm:items-center"> 
            <div class=" text-sm">
              <p class="my-5 text-base text-center"><b>{{name}}</b></p>            
              <p v-if="!name" class="my-5 text-base text-gray-500 text-center">{{nameDefault}}</p>
              <p class="my-5 text-left"><b>Telefone: </b> {{tel}}</p>
              <p class="my-5 text-left"><b>Email: </b>{{Email}}</p>
              <p class="my-5 text-left"><b>Idade: </b>{{idade}}</p>
              <p class="my-5 text-left"><b>Setor: </b>{{sectorSelected}}</p>             
            </div>            
          </div>
          <div class="flex justify-end">
              <img class="w-20" v-if="sectorSelected == 'Relacionamento'" src="../assets/headset.png"/>
              <img class="w-20" v-if="sectorSelected == 'Tecnologia'" src="../assets/coding.png"/>
              <img class="w-20" v-if="sectorSelected == 'Juridico'" src="../assets/balance.png"/>
              <img class="w-20" v-if="sectorSelected == 'Manutencao'" src="../assets/mechanic.png"/>
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
  created(){
    // if(this.setor == this.setores.id){
    //   this.setorName = this.setores.setor;
    // }
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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped> 
   .uploading-image{
     display:flex;
   }
 </style>
