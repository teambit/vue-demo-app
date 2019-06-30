<template>
  <div id="input-container">
        <input
      class="form-control"
      type="text"
      id="input-text"
      v-model="inputValue" placeholder="Insert a task" @keyup.enter="onAdd"
      >
       <button type="button" :disabled="!inputValue" :class=" inputValue ? 'btn btn-primary' : 'btn btn-secondary'" id="add-item" @click="onAdd" >Add</button>
  </div>
</template>

<script>
export default {
  data(){

    return {
      inputValue: ''
    }
  },
  methods :{
    onAdd(){
      if (this.inputValue.replace(/\s/g,'')) {
              this.$emit('onAdd', this.inputValue);
              this.inputValue = '';
      }
    }
  }
}
</script>

<style>

#input-text {
  width: 100%;
  padding: 8px 10px;
  border: 1px solid #007bff;
  display: inline-block;
  flex: 4;
}
#input-container{
  display: flex;
	margin-bottom: 40px;
}
#add-item{
    width: 100%;
    height: 100%;
    margin-left: 10px;
    flex:1;
}

</style>
