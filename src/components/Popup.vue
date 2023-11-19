<template>
    <div class="popup" :class = '{"_active-popup": active}'>
        <div class="popup__container">
            <div class="popup__header">
                <h1 class="popup__title">{{ good.name }}</h1>
                <button class="popup__close-btn" @click="$emit('close')" ><img src="../assets/img/icons/close.svg"></button>
            </div>
            <div class="popup__body">
                <div class="popup__img"><img :src='imgSrc' alt=""></div>
                <div class="popup__info info">
                    <p class="info__text">{{ good.text}}</p>
                </div>
            </div>
            <div class="popup__footer">
                <button class="popup_add-btn">Добавить</button>
                <div class="popup__count">
                    <button class="minus">-</button>
                    <span>{{ }}</span>
                    <button class="plus">+</button>
                </div>
                <span class="popup__price">{{ good.price }}</span>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Popup",
    emits:['close'],
    props: {
        active: Boolean,
        good: Object
    },
    mounted() {
        console.log(this.good)
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