<template>
  
  <div class="notes__item">

    <div class="notes__item-top" :class="{between: !grid}">
        <h3 class="notes__item-title">{{note.title}}</h3>
        <p class="notes__item-date">{{note.date}}</p>
    </div>

    <p class="notes__item-text">{{note.descr}}</p>

    <div class="notes__item-btns">

        <button class="notes__item-btn edit" @click="$emit('changeNote', note.id)">
            <img src="@/assets/img/edit.svg" alt="">
            <span>O'ZGARTIRISH</span>
        </button>

        <button class="notes__item-btn del" @click="$emit('delNote', note.id)">
            <img src="@/assets/img/delete.svg" alt="">
            <span>O'CHIRISH</span>
        </button>
    </div>


  </div>
 

</template>

<script>
export default {

    props: {
        grid: Boolean,
        note: Object
    }

}
</script>

<style>

.notes__item{
   background: #f3edf7;
   border: 2px solid red;
   padding: 16px;
   border-radius: 16px;
   box-shadow: 0px 1px 3px 1px #00000026;
   box-shadow: 0px 1px 2px 0px #0000004D;
}

.notes__item-title{
    font-family: 'Roboto-Medium';
    line-height: 24px;
    letter-spacing: 0.1px;
}

.notes__item-date{
    color: #CAC4D0;
    font-size: 14px;
    line-height: 20px;
    letter-spacing: 0.25px;
}

.notes__item-text{
    font-size: 14px;
    line-height: 20px;
    font-family: 'Roboto-Regular';
    color: #49454F;
    margin: 16px;
}

.notes__item-btns{
    display: flex;
    justify-content: flex-end;
    gap: 15px;
}

.notes__item-btn{
    display: flex;
    align-items: center;
    gap: 10px;
    background: transparent;
    padding: 12px;
    border-radius: 5px;
}

.edit{
    color:  #6750A4;
    font-weight: bold;
    transition: 0.5s;
}

.edit:hover{
  background: #E6DDFF;
}


.del{
    color: #CF1B1B;
    font-weight: bold;
}

.del:hover{
  background: #FFE1E1;
}

.between{
    display: flex;
    justify-content: space-between;
    align-items: center;
}







</style>