<template>
    <div class="grid grid-cols-1 lg:grid-cols-2 ">
      <div class="bg-blue-600 min-h-screen h-fit lg:flex  px-8 pb-[40rem] sm:p-12 justify-center" >
        <div class="lg:w-3/4 sm:h-full">
          <header>
            <h1 class="text-white text-center  title">Crie seu crachá</h1>
            <p class="text-center text-blue-200 subtitle">Em poucos dias você o receberá em casa</p>
          </header>
          <form action="" class="h-16 sm:h-11  mt-8">
            <input v-model="name" placeholder="Nome" type="text" class="input w-full">
            <input v-model="tel"  @keypress="onlyNumber" maxlength="11"  placeholder="Telefone" type="text" class="input w-full">
            <input v-model="email" id="email" placeholder="Email" type="text" class="input w-full" :class="showEmailErro() ? 'input-error':'input'">
            <input v-model="age" @keypress="onlyNumber" maxlength="2" placeholder="idade" type="text" class="input w-full" >          
            <div class="lg:flex lg:justify-between">
              <select v-model="sectorSelected"  class="w-full lg:w-1/2 input  cursor-pointer">  
                <option value="" disabled >Setor</option>                         
                <option v-for="sector in sectors" :key="sector.id" :value="sector.name">{{sector.name}}</option>                              
              </select>                  
              <label for="upload-file" class="btn btn-secondary">               
                <span class="flex items-center ">Escolha sua foto</span>
                <input type="file" id="upload-file" hidden @change="uploadImage"/>
              </label>            
            </div>                    
            <button @click.stop.prevent="finishForm" :disabled="!allFieldsFilled"  class="btn w-full sm:w-1/2" :class="allFieldsFilled ?'btn-primary' : 'btn-disabled'">Pronto!</button>
          </form>    
        </div>                      
      </div>

      <div class=" flex  py-5 px-12 lg:px-24 xl:px-48 xl:py-14 bg-slate-200 relative">
        <Card :name="name" :tel="tel" :email="email" :age="age" :sectorSelected="sectorSelected" :previewImage="previewImage" :sucess="showSucess" />
      </div>
    </div>      
</template>

<script>
import Card from '../components/Card.vue'


export default {
  img:'imageUpload',
  components: {
    Card,    
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
        {id:3,name:'Jurídico'},
        {id:4,name:'Manutenção'},
      ],      
    })
    
  }, 
   methods:{
      chooseFiles(){ 
              document.getElementById("fileUpload").click();
            },
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
            validEmail: function (email) {
              var re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
              return re.test(email);
            },  
            showEmailErro(){
              const inputEmail = document.getElementById('email');              
              if(this.email.length > 0) return !this.validEmail(this.email)               
            },     
             
            CheckFieldsFilled(){                                
                this.allFieldsFilled = 
                  this.name.length > 0 && 
                  this.validEmail(this.email) &&
                  this.sectorSelected.length > 0 && 
                  this.age > 0 &&
                  this.photoChoosed == true;                               
            },
            onlyNumber ($event) {              
              let keyCode = ($event.keyCode ? $event.keyCode : $event.which);
              if ((keyCode < 48 || keyCode > 57) && keyCode !== 46) { 
                 $event.preventDefault();
              }
            },
           
            finishForm(){              
              this.showSucess = true;               
              this.scrollToElement({behavior: 'smooth'})              
              setTimeout(() => {
                document.location.reload(true);
              }, 7000)                            
            },
            scrollToElement(options){
              const el = document.getElementById('card');
              console.log(el)
              if (el) {
                el.scrollIntoView(options);
              }
            }
  },
  updated(){
    this.CheckFieldsFilled()
  },                
}
</script>


<style scoped> 

 </style>
