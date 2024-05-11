<template>

<div class="notes">
    <div class="container">

        <div class="notes__top">

            <h2 class="notes__title">{{notes.length > 0 ? 'Barcha Eslatmalar' : 'Eslatmalar yo`q'}}</h2>


            <button class="notes__btn" @click="grid = !grid">
                <img src="@/assets/img/Vector.svg" alt="" v-if="grid">
                <img src="@/assets/img/setka.svg" alt="" v-else>
                <span>{{grid ? "Ro'yhat" : "Setka"}}</span>
            </button>

        </div>


        <div class="notes__list" :class="{active: !grid}">

            <NoteItem 
            :grid ="grid"
            v-for="note in notes"
            :key="note.id"
            :note="note"
            @delNote="$emit('delNote', note.id)"
            @changeNote="$emit('changeNote', note.id)"
            />

        </div>
    </div>
</div>
  

</template>

<script>

import NoteItem from '@/components/NoteItem.vue'


export default {

    components: {
        NoteItem
    },

 data(){
    return {
        grid: true
    }
 },

 props: {
    notes: {
        typeof: Array , 
        required: true
    }
 }

}
</script>

<style>

.notes{
    margin-top: 30px;
}

.notes__top{
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.notes__title{
    font-size: 22px;
    color:  #323232;
    line-height: 28px;
}

.notes__btn{
    outline: none;
    background: #f3edf7;
    width: 120px;
    height: 56px;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 15px;
    border: 2px solid red;
    border-radius: 16px;
}

.notes__btn span{
  font-size: 14px;
  font-family: 'Roboto-Medium';
  line-height: 20px;
  color: #6750A4;
}

.notes__list{
    margin-top: 50px;
    display: grid;
    grid-template-columns: repeat(3,1fr);
    gap: 24px;
}

.notes__list.active{
    grid-template-columns: 1fr;
}




</style>