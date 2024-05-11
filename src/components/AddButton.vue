<template>
  
<button class="add__btn" @click="$emit('openModal')">
    <img src="@/assets/img/edit.svg" alt="">
</button>

</template>

<script>
export default {

}
</script>

<style>

.add__btn{
  background: #f3edf7;
  width: 56px;
  height: 56px;
  position: fixed;
  right: 30px;
  bottom: 30px;
  border: 2px solid red;
  border-radius: 16px;
  cursor: pointer;
}


</style>