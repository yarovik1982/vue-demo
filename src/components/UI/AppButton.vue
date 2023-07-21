<template>
   <button>
      <slot></slot>
   </button>
</template>
<script>
export default {
   name:'app-button',
  components: {},
  data() {
    return {
    };
  },
};
</script>
<style scoped>
button{
  background-color: transparent;
  border:1px solid teal;
  padding: 4px 8px;
}

</style>>


