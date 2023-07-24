<template>
   <div class="dialog" 
      v-if="show"
      @click="hideDialog"
   >
      <div class="dialog-content" @click.stop>
         <slot></slot>
      </div>
   </div>
</template>

<script>
export default {
   name:'app-dialog',
   props:{
      show:{
         type:Boolean,
         default:false,
      }
   },
   methods:{
      hideDialog(){
         this.$emit('update:show', false)
      }
   },
}
</script>

<style scoped>
.dialog{
   top: 0;
   left: 0;
   bottom: 0;
   right: 0;
   position: fixed;
   background-color: rgba(0,0,0,.5);
   display: flex;
}
.dialog-content{
   background-color: #fff;
   margin: auto;
   border-radius: 16px;
   min-width: 300px;
   min-height: 50px;
}
</style>