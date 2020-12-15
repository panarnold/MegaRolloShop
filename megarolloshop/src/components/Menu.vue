<template>
    <div>
        <div :key="item.id" v-for="item in menu">
            <Item :item="item" @add-to-cart="addToCart(item)"/>
        </div>
    </div>
</template>

<script>
import Item from './Item.vue';

export default {
    name: "Menu",
    emits: [
        "add-to-cart"
    ],
    components: {
        Item
    },
    props: ["menu"],
    methods: {
        addToCart(item) {
            console.log(item);
            this.$emit("add-to-cart", item);
        }
    }
    
}
</script>

<style scoped>

</style>