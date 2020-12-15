<template>
    <div class="item">
        <h1>Your Cart:</h1>
        
        <div v-for="item in list" :key="item.id">
           <h3> <input type="checkbox"/>{{item.name}}: {{item.price}} 
           <button @click="$emit('remove-item', item.id)">Remove</button></h3>
           
        </div>
        <div>
            <h2>Total: PLN</h2>
        </div>
        <!-- <button @click="removeCertain">Remove certain dishes</button> -->
        <button @click="$emit('remove-all')">Clear the cart</button>
    </div>
</template>

<script>
export default {
    name: "Cart",
    props: {
        list: {
            type: Array,
            required: true
        }
    },
    emits: [
        "remove-item"
    ]
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