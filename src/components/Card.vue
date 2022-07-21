<template>
    <div class="card">
        <div>
            <input type="checkbox">
            <p>{{ task }}</p>
        </div>
        <div id="remove" @click="$emit('remove')">
            <fa icon="fa-solid fa-xmark" />
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Card',
        props: ['task'],
        emits: ['remove']
    }
</script>

<style scoped>
.card {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 30px;
    border: 1px solid rgb(149, 149, 149);
    padding: 5px 10px;
    margin: 5px 0;
}
.card > div {
    display: flex;
}
.card > #remove {
    cursor: pointer;
} 
.card > div > p {
    margin: 0 10px;
}
.card > div > input:checked + p {
    text-decoration: line-through;
    text-decoration-thickness: 1px;
    color: rgb(129, 129, 129);
}
</style>