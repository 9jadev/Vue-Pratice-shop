<template>
    <ul class="list-group">
        <li :key="item.id" class="list-group-item" v-for="item in items">
            {{item.title}} - &#x20A6; {{item.price}}

            <button @click="$emit('remove-from-cart', item)" class="btn badge badge-danger float-right">
                Remove from Cart.
            </button>
        </li>
    </ul>
</template>

<script>
    export default {
        props : ['items']
    }
</script>

<style scoped>

</style>