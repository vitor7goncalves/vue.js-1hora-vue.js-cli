<template>
  <div class="container">
        <h1>Comentários</h1>
        <hr />
       <FormTodo  v-on:addTodo='addComment' ></FormTodo>
       <p v-if='comments.length <= 0'>0 comentários</p>
       <p v-else-if='comments.length === 1'>1 comentários</p>
       <p v-else-if='comments.length === 2'>2 comentários</p>
       <p v-else-if='comments.length === 3'>3 comentários</p>
       <p v-else-if='comments.length === 4'>4 comentários</p>
       <p v-else-if='comments.length === 5'>5 comentários</p>
       <p v-else-if='comments.length === 6'>6 comentários</p>
       <p v-else-if='comments.length === 7'>7 comentários</p>
       <p v-else-if='comments.length === 8'>8 comentários</p>
       <p v-else-if='comments.length === 9'>9 comentários</p>
       <p v-else-if='comments.length === 10'>10 comentários</p>
       <p v-else-if='comments.length >= 11'>Mais de 10 comentários</p>
        <div class="list-group">
            <div  class="list-group-item" v-for="(comment, index) in allComments" :key="comment">
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
import FormTodo from './FormTodo'
export default {

components: {
    FormTodo
},

data() {
          return {
             comments: [
                
             ],
            
      }
    },
      methods: {
          addComment(comment){
             this.comments.push(comment)
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

