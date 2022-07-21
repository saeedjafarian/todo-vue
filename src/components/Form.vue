<template>
    <div>
        <form @submit.prevent>
            <div>
                <input type="text" placeholder="Add a task" v-model="task">
                <button @click="addTask(); $emit('update');">
                    <fa icon="fa-solid fa-arrow-down" />
                </button>
            </div>
        </form>
    </div>
</template>

<script>
    import axios from 'axios'
    export default {
        name: 'Form',
        data() {
            return {
                task: '',
            }
        },
        emits:['update'],
        methods: {
            addTask() {
                axios.post('http://localhost:3000/tasks', {title: this.task});
                this.task = '';
            }
        }
    }
</script>

<style scoped>
form > div {
    position: relative;
}
form > div > input[type=text] {
    width: 360px;
    height: 30px;
    padding: 0 15px;
    font-size: 0.9rem;
    border: 2px solid rgb(139, 139, 139);
    outline: none;
}
form > div > input[type=text]:focus {
    border: 2px solid rgb(27, 179, 131);
}
form > div > button {
    padding: 0;
    width: 33px;
    height: 33px;
    background-color: rgb(27, 179, 131);
    position: absolute;
    top: 0;
    right: 0;
    border-radius: 0;
    font-size: 15px;
    color: #eee;
}
</style>