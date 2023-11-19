<template>
    <nav class="nav">
        <div class="container">
            <ul class="nav__items">
                <NavItem
                    v-for="(item, index) in items"
                    :item = 'item'
                    :key = 'index'
                    @click="$emit('change', index)"
                />
            </ul>
        </div>
    </nav>
</template>

<script>
import NavItem from './NavItem.vue'
export default {
    name: "Nav",
    emits: ['change'],
    props:{
        items: Array,
        activeNum: Number
    },
    components: {
        NavItem
    },
}
</script>
<style scoped>

</style>