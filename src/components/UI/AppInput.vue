<template>
   <input type="text"
      :value="modelValue"
      @input="updateInput"
   />
</template>
<script>
export default {
   name:'app-input',
   props:{
      modelValue:[String, Number],
   },
   methods:{
      updateInput(event){
         this.$emit('update:modelValue', event.target.value)
      },
   },
}
</script>

<style scoped>
input{
  width: 100%;
  padding: 4px 16px;
  outline: none;
  border: 2px solid teal;
}
</style>