<template>
    <li class="good">
        <div class="good__img">
            <img  :src= "imgSrc" alt="" srcset="">
        </div>
        <div class="good__info">
            <p class="good__name">{{ cartGood.name }}</p>
            <span class="good__weight">{{ cartGood.weight }}г</span>
            <span class="good__price">{{ cartGood.price }}₽</span>
        </div>
        <div class="good__count">
            <button class="minus">-</button>
            <span>{{ cartGood.count }}</span>
            <button class="plus">+</button>
        </div>
    </li>
</template>

<script>
export default {
    name: "CartItem",
    props: {
        cartGood: Object,
    },
    computed: {
        imgSrc(){
            return new URL(`../assets/img/${this.cartGood.productImg}`, import.meta.url).href
        }
    }
}
</script>

<style scoped>

</style>