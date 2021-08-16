<template>
    <li>
        <span v-bind:class="{done: t.completed}">
            <input type="checkbox" v-on:change="t.completed = !t.completed">
            <strong>{{index + 1}}</strong>
            {{t.title | uppercase}}
        </span>
        <button class="rm" v-on:click="$emit('remove-todo', t.id)">&times;</button>
    </li>
</template>

<script>
export default {
    props: {
        t: {
            type: Object,
            required: true
        },
        index: Number
    },
    filters: {
        uppercase(value) {
            console.log(value)
            return value.toUpperCase()
        }
    }
}
</script>

<style scoped>
    li {
        border: 4px solid seagreen;
        display: flex;
        justify-content: space-between;
        padding: 20px;
        margin-bottom: 5px;
    }

    .rm {
        background:teal;
        color: #fff;
        border-radius: 20%;
        font-weight: bold;
    }

    .done {
        text-decoration: line-through;
    }
</style>