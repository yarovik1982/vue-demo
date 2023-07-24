<template>
  <select :v-model='modelValue' @change="changeOption" name="select">
    <option disabled selected>Выберите из списка</option>
    <option 
      v-for="option in options"
      :key="option.value"
      :value="option.value"
      
    >
      {{option.name}}
    </option>
  </select>
</template>
<script>
export default {
  name: "app-select",
  components: {},
  props:{
   modelValue:{
      type:String,
   },
   options:{
      type:Array,
      default:() => []
   }
  },
  data() {
    return {};
  },
  methods: {
   changeOption(event){
      this.$emit('update:modelValue', event.target.value)
   }
  },
};
</script>
<style></style>
