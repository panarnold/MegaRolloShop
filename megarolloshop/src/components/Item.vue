<template>
    <div class="item">
        <p>{{item.id}}. {{item.name}}:{{item.price}}PLN <button @click="$emit('add-to-cart',item)">Add to cart</button></p>
    </div>
</template>

<script>
export default {
    name: "Item",
    emits: [
        "add-to-cart"
    ],
    props: ["item"]

    
}
</script>

<style scoped>
    .item {
        background: rgba(9, 51, 190, 0.267);
        text-align: left;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }
</style>