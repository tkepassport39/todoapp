<template>
    <div>
        <form @submit="addTodo">
            <v-text-field v-model="title" name="title" label="Add Todo Item"></v-text-field>
            <!-- <input type="text" v-model="title" name="title" placeholder="Add Todo Item..."> -->
            <v-btn color="primary" tile type="submit" value="submit">Submit</v-btn>
            <!-- <input type="submit" value="submit" class="btn"> -->
        </form>
    </div>
</template>

<script>
export default {
    name: "AddTodo",
    data() {
        return {
            // used in v-model
            title: ''
        }
    },
    methods: {
        addTodo(e){
            e.preventDefault();
            const newTodo = {
                title: this.title,
                completed: false
            }
            // send up to parent app.vue
            this.$emit('add-todo', newTodo);
            // clear the form
            this.title = '';
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
    }
    
    input[type="text"]{
        flex: 10;
    }

    input[type="submit"]{
        flex: 2;
    }

    .v-btn {
        width: 30%;
        float: right;
    }

    .v-btn:not(.v-btn--round).v-size--default {
        height: 49px;
    }

    .v-text-field{
        padding-left: 6px;
    }

</style>