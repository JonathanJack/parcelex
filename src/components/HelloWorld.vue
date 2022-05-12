<template>
  <div class="hello">
  <p>{{name}}</p>
  <p>{{tel}}</p>
  <p>{{email}}</p>
  <p>{{age}}</p>
  
  <input v-model="name" placeholder="name" />
  <input v-model="tel" placeholder="tel" />
  <input v-model="email" placeholder="email" />
  <input v-model="age" placeholder="age" />

  <img :src="previewImage" class="uploading-image" />
  <input type="file" accept="image/jpeg" @change=uploadImage>
  
    
  </div>
</template>

<script>
export default {
  img:'imageUpload',
  data(){
    return({
      name: '',
      tel: '',
      email: '',
      age: '',
      previewImage:null
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
