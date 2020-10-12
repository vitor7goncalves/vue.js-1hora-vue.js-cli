<template>
     <div class="form-todo form-group">
            <p>
                <input v-model="name" type="text" class="form-control" placeholder="Nome" aria-label="Nome" aria-describedby="basic-addon1">
            </p>
            <p>
                <textarea v-model="message" placeholder="Escreva seu comentário..."  class="form-control" aria-label="With textarea" name="author"></textarea>
            </p>
            <p>
                <button @click="addComment" type="submit" class="btn btn-primary">Comentar</button>
            </p>
        </div>
</template>

<script>
export default {
    data() {
        return {
            name: '',
            message:'',
        }
    },

    methods: {
        
    
          addComment(){
              if(this.message.trim() === ''){
                  return;
              }

            this.$emit('addTodo',{
                name: this.name,
                message: this.message,
            });

              this.name = "";
              this.message = "";
          },
    },
}
</script>