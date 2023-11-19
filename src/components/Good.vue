<template>
    <li class="product__item">
        <div class="product__img"
             @click="$emit('pop', good)">
            <img :src = "imgSrc" alt="">
        </div>
        <h3 class="product__price">{{ good.price }}</h3>
        <p class="product__name">{{ good.name }}</p>
        <span class="product__weight">{{ good.weight }}г</span>
        <button class="add-btn"
                @click = "$emit('addCart', good)"
        >Добавить</button>
    </li>
</template>

<script>
export default {
    name: "Goods",
    props: {
        good: {
            name: String,
            price: Number,
            weight: Number,
            productImg: String
        }
    },
    data() {
        return {
            disabled: false,
        }
    },
    computed: {
        imgSrc(){
            return new URL(`../assets/img/${this.good.productImg}`, import.meta.url).href
        }
    }
}
</script>

<style scoped>

</style>