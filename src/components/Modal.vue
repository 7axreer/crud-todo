<template>
  
<Transition name="modal">

<div class="modal" @click="closeModal">

    <div class="modal__block" @click.stop>
        <h2 class="modal__title">
            {{ edit ? 'Eslatmani tahrirlash' : 'Eslatmani qo`shish'}}
        </h2>

        <div class="modal__inputs">
            <label>
                <span>Title</span>
                <input type="text" v-model="title">
            </label>
            <label>
                <span>Content</span>
                <textarea v-model="descr"></textarea>
            </label>
        </div>

        <div class="modal__btns">
            <button class="modal__btn cancel" @click="closeModal">Bekor qilish</button>
            <button v-if="!edit" class="modal__btn add" @click="addNote">Qo'shish</button>
            <button v-else class="modal__btn add" @click="changeNote">O'zgartirish</button>
        </div>


    </div>
</div>

</Transition>

</template>

<script>
export default {
   data(){
    return {
        title: ' ',
        descr: ' ',
    }
   },

   props: {
     currentId: Number,
     edit: Boolean,
     editNote: Object
   },

   methods: {
     closeModal(){
        this.$emit('closeModal', false),
        this.title = ' ';
        this.descr = ' ';
     },

     addNote(){
     if(this.title != ' ' && this.descr != ' '){
        const item = {
            id: this.id,
            title: this.title,
            descr: this.descr,
            date: new Date().toLocaleDateString()
        }
        this.$emit('addNote', item);
        this.title = ' ';
        this.descr = ' ';
     }
            
     },

     changeNote(){
         if(this.title != ' ' && this.descr != ' '){
            const editedNote = {
                id: this.editNote.id,
                title: this.title,
                descr: this.descr,
                date: new Date().toDateString()
            }
            this.$emit('editedNote', editedNote)
            this.closeModal()
         }
     }
   }
}
</script>

<style>

.modal{
 background: rgba(0, 0, 0, 0.35);
 top: 0;
 left: 0;
 bottom: 0;
 right: 0;
 position: fixed;
 display: flex;
 justify-content: center;
 align-items: center;
}

.modal__block{
    max-width: 312px;
    width: 100%;
    padding: 24px;
    border-radius: 28px;
    background: linear-gradient(0deg, #FFFBFE, #FFFBFE),
linear-gradient(0deg, rgba(103, 80, 164, 0.11), rgba(103, 80, 164, 0.11));

}

.modal__title{
    color: #1C1B1F;
    font-family: 'Roboto-Regular';
    font-size: 24px;
    line-height: 32px;
    margin-bottom: 16px;
}

.modal__inputs{
    display: flex;
    flex-direction: column;
    gap: 16px;
}

.modal__inputs label {
    position: relative;
}

.modal__inputs span {
    position: absolute;
    left: 16px;
    top: 8px;
    font-size: 12px;
    color: #6750A4;
}

.modal__inputs input ,
.modal__inputs textarea {
    background: #E7E0EC;
    border-radius: 4px 4px 0 0;
    width: 100%;
    border: none;
    outline: none;
    padding: 23px 0 9px 16px;
    line-height: 24px;
    color: #49454F;
    border-bottom: 1px solid black;
    resize: none;
}


.modal__btns{
    display: flex;
    justify-content: flex-end;
    gap: 10px;
    margin-top: 25px;
}


.modal__btn{
    font-size: 14px;
    line-height: 20px;
    font-family: 'Roboto-Medium';
    background: transparent;
    padding: 10px 12px;
    text-transform: uppercase;
    transition: 0.5s;
}

.cancel{
    color: #CF1B1B;
}

.cancel:hover{
    background: #FFE1E1;
}

.add{
  color: #6750A4;
}

.add:hover{
  background: #E6DDFF;
}



.modal-enter-active,
.modal-leave-active {
  transition:  0.3s linear;
}

.modal-enter-from,
.modal-leave-to {
  opacity: 0;
  transform: scale(1.5);
}


</style>