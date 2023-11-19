<template>
    <Header/>
    <Nav :items="items"
         @change="changeCategory"
         :activeNum='activeNum'/>

    <Main :title="items[this.activeNum].name"
          :goods = 'goods[items[activeNum].name]'
          :cart = 'cart'
          @pop = 'popup'
          @add-cart = 'addCart'
    />
    <Popup @close = 'closePopup'
           :good= "popupInfo"
           :active = 'popupActive'
    />
</template>

<script>
import Nav from "@/components/Nav.vue";
import Main from "@/components/Main.vue";
import Header from "@/components/Header.vue";
import Popup from "@/components/Popup.vue";

export default {
    name: "Home",
    components: {Header, Main, Nav, Popup},
    data() {
        return {
            items: [{name: 'Бургеры', active: true},
                {name: 'Закуски', active: false},
                {name: 'Хот-доги', active: false},
                {name: 'Комбо', active: false},
                {name: 'Шаурма', active: false},
                {name: 'Пицца', active: false},
                {name: 'Вок', active: false},
                {name: 'Десерты', active: false},
                {name: 'Соусы', active: false}],
            activeNum: 0,
            goods: {
                "Бургеры": [{
                    name: 'Мясная бомба',
                    price: 689,
                    weight: 520,
                    productImg: "burger-item-1.jfif",
                    text: "Супер мясное наслаждение! Большая рубленая котлета из свежего говяжего мяса покорит вас своей сочностью, а хрустящие листья салата добавят свежести."
                },
                    {
                        name: 'Супер сырный',
                        price: 550,
                        weight: 512,
                        productImg: "burger-item-2.png",
                        text: "Супер мясное наслаждение! Большая рубленая котлета из свежего говяжего мяса покорит вас своей сочностью, а хрустящие листья салата добавят свежести."
                    },
                    {
                        name: 'Сытный',
                        price: 639,
                        weight: 580,
                        productImg: "burger-item-3.png",
                        text: "Супер мясное наслаждение! Большая рубленая котлета из свежего говяжего мяса покорит вас своей сочностью, а хрустящие листья салата добавят свежести."
                    },
                    {
                        name: 'Тяжелый удар',
                        price: 480,
                        weight: 470,
                        productImg: "burger-item-4.png",
                        text: "Супер мясное наслаждение! Большая рубленая котлета из свежего говяжего мяса покорит вас своей сочностью, а хрустящие листья салата добавят свежести."
                    },
                    {
                        name: 'Вечная классика',
                        price: 450,
                        weight: 450,
                        productImg: "burger-item-5.png",
                        text: "Супер мясное наслаждение! Большая рубленая котлета из свежего говяжего мяса покорит вас своей сочностью, а хрустящие листья салата добавят свежести."
                    },
                    {
                        name: 'Итальянский',
                        price: 560,
                        weight: 510,
                        productImg: "burger-item-6.png",
                        text: "Супер мясное наслаждение! Большая рубленая котлета из свежего говяжего мяса покорит вас своей сочностью, а хрустящие листья салата добавят свежести."
                    },
                ],
                "Закуски": [{
                    name: 'Начос',
                    price: 250,
                    weight: 220,
                    productImg: "snack-item-1.png",
                    text: "Супер мясное наслаждение! Большая рубленая котлета из свежего говяжего мяса покорит вас своей сочностью, а хрустящие листья салата добавят свежести."
                },
                    {
                        name: 'Картошка фри',
                        price: 245,
                        weight: 180,
                        productImg: "snack-item-2.png",
                        text: "Супер мясное наслаждение! Большая рубленая котлета из свежего говяжего мяса покорит вас своей сочностью, а хрустящие листья салата добавят свежести."
                    },
                    {
                        name: 'Луковые кольца',
                        price: 230,
                        weight: 160,
                        productImg: "snack-item-3.png",
                        text: "Супер мясное наслаждение! Большая рубленая котлета из свежего говяжего мяса покорит вас своей сочностью, а хрустящие листья салата добавят свежести."
                    },
                    {
                        name: 'Домашний хот-дог',
                        price: 290,
                        weight: 250,
                        productImg: "snack-item-4.png",
                        text: "Супер мясное наслаждение! Большая рубленая котлета из свежего говяжего мяса покорит вас своей сочностью, а хрустящие листья салата добавят свежести."
                    },
                    {
                        name: 'Жгучий хот-дог',
                        price: 239,
                        weight: 245,
                        productImg: "snack-item-5.png",
                        text: "Супер мясное наслаждение! Большая рубленая котлета из свежего говяжего мяса покорит вас своей сочностью, а хрустящие листья салата добавят свежести."
                    },
                    {
                        name: 'Классический хот-дог',
                        price: 220,
                        weight: 215,
                        productImg: "snack-item-6.png",
                        text: "Супер мясное наслаждение! Большая рубленая котлета из свежего говяжего мяса покорит вас своей сочностью, а хрустящие листья салата добавят свежести."
                    },
                ]
            },
            cart: [],
            popupActive: false,
            popupInfo: {}
        }
    },
    methods: {
        changeCategory(index) {
            let prev = this.activeNum;
            this.items.forEach((item, ind) => {
                if (ind === prev) {
                    item.active = false;
                }
                if (ind === index) {
                    item.active = true;
                    this.activeNum = index;
                }
            })
        },
        popup(good){
            console.log(good)
            this.popupActive = true
            document.body.classList.add('unscroll')
            this.popupInfo = {...good}
        },
        closePopup(){
            this.popupActive = false
            document.body.classList.remove('unscroll')
            this.popupInfo = {}
        },
        addCart(good){
            if(this.cart.find(item => item === good)){
                return this.cart = this.cart.filter((item) => item !== good)
            }
            else this.cart = [...this.cart, good];
        }
    },
    mounted() {
        window.addEventListener('load', function(){document.body.classList.remove('loading')})
    }
}
</script>

<style scoped>

</style>