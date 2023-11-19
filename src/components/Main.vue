<template>
    <main class="main">
        <div class="container main__container">
            <aside class="card">
                <div class="card__container"
                     @click = "openCart"
                     :class="{'_active-card' : cartActive}">
                    <div class="card__title">
                        <h3 >Корзина</h3>
                        <span >{{ cart.length }}</span>
                    </div>
                    <div v-if="cart.length > 0" class="card__body">
                        <ul class="card__goods goods">
                            <CartItem v-for="(item, index) in cart"
                                      :cartGood="item"
                            />
                        </ul>
                        <div class="card__amount">
                            <h4>Итого</h4>
                            <span>{{ productCount }}</span>
                        </div>
                        <button class="order-btn">Оформить заказ</button>
                        <div class="card__delivery">
                            <img src="../assets/img/icons/Доставка.svg" alt="">
                            <span>Бесплатная доставка</span>
                        </div>
                    </div>
                </div>
            </aside>
            <section class="product">
                <div class="product__container">
                    <h1 class="product__category">
                        {{ title }}
                    </h1>
                    <ul class="product__items">
                        <Good
                            v-for="(good, index) in goods"
                            :good = 'good'
                            @pop="$emit('pop', good)"
                            @add-cart = "$emit('addCart', good)"
                        />
                    </ul>
                </div>
            </section>
        </div>
    </main>
</template>

<script>
import Good from "./Good.vue";
import NavItem from "@/components/NavItem.vue";
import CartItem from "@/components/CartItem.vue";
export default {
    name: "Main",
    emits:['pop', 'onOpen', 'addCart'],
    props: {
        title: String,
        goods: Array,
        cart: Array,
    },
    components: {
        NavItem,
        Good,
        CartItem
    },
    data() {
        return {
            productCount: 2,
            cartActive: false
        }
    },
    methods: {
        openCart(){
            if(this.cart.length > 0 && window.innerWidth <= 785){
                this.cartActive = !this.cartActive;
            }
        },
    },
    computed: {
        productCount(){
            let count = 0;
            this.cart.forEach(item => count += item.price)
            return count;
        }
    }
}
</script>

<style scoped>

</style>