<template>

    <v-card
        class="mx-auto"
        
    >
        <!-- add is-complete class if it is true-->
        <div class="todo-item" v-bind:class="{'is-complete':todoPerItem.completed}">
            <v-list-item-group>
                <v-list-item>

                    <template>
                        <div>
                        <v-list-item-action>
                            <v-checkbox v-on:change="markComplete"></v-checkbox>
                        </v-list-item-action>
                        </div>
                        <v-list-item-content>
                            <v-list-item-title>{{ todoPerItem.title }}</v-list-item-title>
                        </v-list-item-content>
                        
                        <!-- call the method to mark as complete-->
                        <!-- <input type="checkbox" v-on:change="markComplete">
                        {{todoPerItem.title}} -->
                        <!-- emit todo item id as a payload as it needs to go back to app.vue -->
                        <v-btn color="error" fab x-small dark @click="$emit('del-todo', todoPerItem.id)" class="del"><v-icon dark>{{icons.mdiDelete}}</v-icon>
                        </v-btn>
                        <!--<button @click="$emit('del-todo', todoPerItem.id)" class="del">x</button>-->
                    </template>
                </v-list-item>
            </v-list-item-group>
        </div>
    </v-card>
</template>

<script>
import {mdiDelete} from "@mdi/js";

    export default {
        name:"TodoItem",
        props: ["todoPerItem"],
        methods: {
            markComplete(){
                this.todoPerItem.completed = !this.todoPerItem.completed;
            }
        },
        data() {
            return {
                icons: {
                    mdiDelete
                }
            }
        }
    }
</script>

<style scoped>
    .todo-item {
        background: #f4f4f4;
        padding: 0px;
        border-bottom: 1px #ccc dotted;
    }

    .is-complete {
        text-decoration: line-through;
    }

    .del {
        background: red;
        color: #fff;
        border: none;
        padding: 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }
</style>