<template> 

<FormulateForm
    v-model="values"
    @submit="handleLogin"
    @submit.prevent="uploadPhoto"
  >
    <h2>Upload Form</h2>
    <Input type="text" name="description" label="Description" validation="required" />
    <Input type="text" name="photo" label="Photo Upload" validation="required" />
   
    <Input type="submit" label="Upload" />
   
  </FormulateForm>
</template>

<script>
import { defineComponent } from '@vue/composition-api'

export default defineComponent({
    setup() {
        
    },
})


let uploadForm = document.getElementById('uploadForm');
let form_data = new FormData(uploadForm);

fetch("/api/upload", {
 method: 'POST'
 body: form_data
 headers: {
 'X-CSRFToken': this.csrf_token
 }
})
    .then(function (response) {
        return response.json();
    })
    .then(function (data) {
    // display a success message
        console.log(data);
     })
    .catch(function (error) {
    console.log(error);
    });



getCsrfToken() {
 let self = this;
 fetch('/api/csrf-token')
 .then((response) => response.json())
 .then((data) => {
 console.log(data);
 self.csrf_token = data.csrf_token;
 })
 }

data() {
 return {
 csrf_token: ''
 }
}
</script>

