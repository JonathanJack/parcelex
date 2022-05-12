<template>
  <div class="hello">
    <!-- <p>{{name}}</p>
    <p>{{tel}}</p>
    <p>{{email}}</p>
    <p>{{age}}</p>
    
    <input v-model="name" placeholder="name" />
    <input v-model="tel" placeholder="tel" />
    <input v-model="email" placeholder="email" />
    <input v-model="age" placeholder="age" />
  
    <img :src="previewImage" class="uploading-image" />
    <input type="file" accept="image/jpeg" @change=uploadImage> -->

    <div class="grid grid-cols-1 lg:grid-cols-2">
      <div class="bg-blue-600 lg:min-h-screen lg:flex  p-8 sm:p-12 justify-center" >
        <div class="w-3/4">
          <h1 class="text-white text-center text-2xl sm:text-5xl mb-2">Crie seu crachá</h1>
          <p class="text-center text-blue-200 sm:text-lg">Em poucos dias você o receberá em casa</p>

          <form action="" class="  mt-8">
          <input v-model="name" placeholder="Nome" type="text" class="flex-1 h-11 w-full my-4 text-center text-gray-700 bg-gray-200 rounded-md hover:bg-hite border border-gray-200 outline-none">
          <input v-model="tel" placeholder="Telefone" type="number" class="flex-1 h-11 w-full text-center my-4 text-gray-700 bg-gray-200 rounded-md hover:bg-hite border border-gray-200 outline-none">
          <input v-model="Email" placeholder="Email" type="text" class="flex-1 h-11 w-full my-4 text-center text-gray-700 bg-gray-200 rounded-md hover:bg-hite border border-gray-200 outline-none">
          <input v-model="idade" placeholder="idade" type="number" class="flex-1 h-11 w-full my-4 text-center text-gray-700 bg-gray-200 rounded-md hover:bg-hite border border-gray-200 outline-none">
          <input v-model="setor" placeholder="Identificação do Setor" type="text" class="flex-1 h-11 w-full text-center my-4 text-gray-700 bg-gray-200 rounded-md hover:bg-hite border border-gray-200 outline-none">

          <!-- <button class="flex-shrink-0"></button> -->
        </form>
        </div>        
      </div>

      <div class="lg:min-h-screen lg:flex lg:items-center p-12 lg:p-24 xl:p-48">
      <div class="flex-grow bg-white shadow-xl rounded-md border border-gray-300 p-8">
         <img :src="previewImage" class="uploading-image sm:flex-shrink-0 mx-auto sm:mx-0 h-24 rounded-full" />
      <input type="file" accept="image/jpeg" @change=uploadImage>
        <img src="../assets/logo.png" alt="Foto de uma pessoa" class="sm:flex-shrink-0 mx-auto sm:mx-0 h-24 rounded-full">
        <div class="sm:flex sm:items-center"> 
          
          <div class="sm:ml-4 sm:text-left text-center">
            <p class="text-xl">{{name}}</p>
            <!-- <p class="text-sm text-gray-600">Um belo de um bom funcionario</p> -->
            <p>{{tel}}</p>
            <p>{{Email}}</p>
            <p>{{idade}}</p>
            <p>{{setor}}</p>
            <div class="mt-">
              <button class="text-red-500 hover:text-white hover:bg-red-500 border-red-500 
              font-semibold rounded-md text-xs px-4 py-1 focus:outline-none"
              >Não é fulaninho?</button>              
            </div>
          </div>
        </div>
        <form action="" class="flex w-full mt-8">
          <input type="text" class="flex-1 w-full text-gray-700 bg-gray-200 rounded-md hover:bg-hite border border-gray-200">
          <button class="flex-shrink-0"></button>
        </form>
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
      name: 'Nome',
      tel: '',
      email: '',
      age: '',
      setor: '',
      previewImage: '../assets/logo.png',
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
            },
            // img(){
            //   return if null ? '../assets/logo.png' : 
            // }

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
