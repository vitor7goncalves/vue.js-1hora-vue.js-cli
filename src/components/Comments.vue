<template>
  <div class="container">
        <h1>Comentários</h1>
        <hr />
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
        <div class="list-group">
            <div  class="list-group-item" v-for="(comment, index) in allComments" :key="comment.name">
               <span class="comment_author">Autor: <strong>{{ comment.name }}</strong></span>
               <p>{{ comment.message }}</p>
               <div>
                   <a href="#" title="Excluir" @click.prevent="removeComment(index)">Excluir</a>
               </div>
            </div>
        </div>
        <hr />
    </div>
</template>

<script>
export default {
data() {
          return {
             comments: [
                
             ],
             name: '',
             message:''
          }
      },
      methods: {
          addComment(){
              if(this.message.trim() === ''){
                  return;
              }

            this.comments.push({
                name: this.name,
                message: this.message,
            })

              this.name = "";
              this.message = "";
          },
          removeComment(index){
              this.comments.splice(index, 1);
          }
      },

      computed: {
          allComments(){
              return this.comments.map(comment => ({
                  ...comment,
                  name: comment.name.trim() === '' ? 'Anônimo' : comment.name,
              }))
          }
      },
}
</script>

<style>

</style>

