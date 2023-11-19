<template>
    <li class="nav__item" >
        <button class="category-btn" :class="{_active: item.active}">
            <img :src="imgSrc" alt="">
            <span>{{ item.name }}</span>
        </button>
    </li>
</template>

<script>
export default {
    name: "NavItem",
    props: {
        item: {
            names: String,
            active: Boolean
        }
    },
    data(){
        return {
            active: false,
        }
    },
    computed: {
        imgSrc(){
            return new URL(`../assets/img/icons/${this.item.name}.svg`, import.meta.url).href
        }
    }
}
</script>

<style scoped>

</style>