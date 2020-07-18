<template>
    <div class="container pt-3">
            <h1>Comments</h1>
            <hr/>
            <FormTodo v-on:add-todo="addComment"></FormTodo>
            <div class="list-group pt-3">
                <p v-if="comments.length <=0">Sem comentários</p>
                    <div v-else class="list-group-item" v-for="(comment, index) in allComments" v-bind:key="index">
                        <span class="comment-author">
                            Author: <strong>{{comment.name}}</strong>
                        </span>
                        <p>{{comment.message}}</p>
                        <div>
                            <a v-on:click.prevent="removeComment(index)" href="#" title="Delete">Delete</a>
                    </div>
                </div>
            </div>
        <hr/>
    </div>

</template>

<script>
import FormTodo from './FormTodo';

    export default{
        components:{
            FormTodo
        },
        data() {
                return{
                    comments: []
                  
                }
            },
            methods: {
                addComment(comment){
                    this.comments.push(comment);
                }, 
                removeComment(index){
                    this.comments.splice(index, 1);
                }
            },
            computed: {
                allComments(){
                    return this.comments.map(comment => ({
                        ...comment,
                        name: comment.name.trim() === '' ? 'Anonymous' : comment.name
                    }))
                }
            },
            watch: {
                comments(val){
                    console.log('val', val)
                }
            }
    }
</script>