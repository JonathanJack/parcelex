<template>
  <div class="hello">
   <Sucess v-if="showSucess"/>


    <div class="grid grid-cols-1 lg:grid-cols-2 ">
      <div class="bg-blue-600 min-h-screen lg:flex  p-8 sm:p-12 justify-center max-h-screen" >
        <div class="lg:w-3/4 sm:h-full">
          <h1 class="text-white text-center  title">Crie seu crachá</h1>
          <p class="text-center text-blue-200 subtitle">Em poucos dias você o receberá em casa</p>
          <form action="" class="  h-16 sm:h-11  mt-8">
          <input v-model="name" placeholder="Nome" type="text" class="input w-full">
          <input v-model="tel"  @keypress="onlyNumber" maxlength="11"  placeholder="Telefone" type="text" class="input w-full">
          <input v-model="email" placeholder="Email" type="text" class="input w-full">
          <input v-model="age" @keypress="onlyNumber" maxlength="2" placeholder="idade" type="text" class="input w-full" >          
          <div class="lg:flex lg:justify-between">
            <select v-model="sectorSelected"  class="w-full lg:w-1/2 input  cursor-pointer">  
              <option value="" disabled >Setor</option>                         
              <option v-for="sector in sectors" :key="sector.id" :value="sector.name">{{sector.name}}</option>                              
            </select>                  
            <label for="upload-file" class="btn btn-secondary flex align-center">               
              <span>Escolha sua foto!</span>
              <input type="file" id="upload-file" hidden @change="uploadImage"/>
            </label>

            
          </div>          
          <button v-on:click="finishForm" :disabled="!allFieldsFilled"  class="btn" :class="allFieldsFilled ?'btn-primary' : 'btn-disabled'">Pronto!</button>
        </form>    
        </div>                  
    
      </div>

      <div class="lg:min-h-screen max-h-screen flex items-center py-5 px-12 lg:px-24 xl:px-48 xl:py-14 bg-slate-200">
        <Card :name="name" :tel="tel" :email="email" :age="age" :sectorSelected="sectorSelected" :previewImage="previewImage" />
      </div>

    </div>

    
    
  </div>
</template>

<script>
import Card from './Card.vue'
import Sucess from './Sucess.vue'

export default {
  img:'imageUpload',
  components: {
    Card,
    Sucess

  },
  data(){
    return({
      name: '',      
      tel: '',
      email: '',
      age: '',      
      allFieldsFilled: false,
      sectorSelected: '',
      photoChoosed: false,
      showSucess: false,
      
      previewImage: null,
      sectors: [
        {id:1,name:'Relacionamento'},
        {id:2,name:'Tecnologia'},
        {id:3,name:'Juridico'},
        {id:4,name:'Manutencao'},
      ],      
    })
    
  }, 
   methods:{
            uploadImage(e){
              
                const image = e.target.files[0];
                const reader = new FileReader();
                reader.readAsDataURL(image);
                reader.onload = e =>{
                    this.previewImage = e.target.result;
                    console.log(this.previewImage);
                };
                this.photoChoosed = true;
            },
            
            chooseFiles(){ 
              document.getElementById("fileUpload").click();
            },
          

            CheckFields(){   
              console.log(this.name.length);           
              
              console.log(this.email.length);  
              console.log(this.age.length);  
              console.log(this.sectorSelected.length);  
              
                this.allFieldsFilled = this.name.length > 0 && this.email.length > 0 && this.sectorSelected.length > 0 && this.photoChoosed == true;
               
                
            },
            onlyNumber ($event) {
              
              let keyCode = ($event.keyCode ? $event.keyCode : $event.which);
              if ((keyCode < 48 || keyCode > 57) && keyCode !== 46) { 
                 $event.preventDefault();
              }
            },
            sucessPopup(){
              this.showSucess = true;
            },
            finishForm(){
              event.preventDefault();
              this.sucessPopup();
              setTimeout(() => {
                document.location.reload(true);
              }, 7000)
              
            }
      },
  updated(){
    this.CheckFields()
  },
        
        
  props: {
    msg: String
  }
}
</script>


<style scoped> 

 </style>
