<template>
    <div class="form-todo form-group text-center ">
            <p>
                <input v-model="name" type="text" placeholder="Name" name="author" class="form-control">
            </p>
            <p>
                <textarea v-model="message" name="message" placeholder="Comment" class="form-control"></textarea>
            </p>
            <button v-on:click="addComment" type="submit" class="btn btn-primary">Submit Comment</button>
        </div>
</template>

<script>
    export default{
        data(){
            return{
                name: '',
                message: ''
            }
        },
        methods:{
               addComment(){
               
                    if( this.message.trim() === ''){
                        return;
                    }

                    this.$emit('add-todo', {
                        name: this.name,
                        message: this.message
                    })
                  
                    this.name = '';
                    this.message = '';
                }
        }
    }
</script>