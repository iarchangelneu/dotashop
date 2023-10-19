<template>
    <div class="page">
        <PrevPage></PrevPage>
        <h1>подтверждение покупки</h1>
        <div class="empty" v-if="cart.length <= 0">
            <h2>Вы пока не добавили предметы в корзину</h2>
            <NuxtLink to="/catalog">Перейти в магазин</NuxtLink>
        </div>
        <div class="cart__body" v-else>
            <div class="catalog__body">
                <div class="catalog__item" v-for="item in cart" :key="item.id"
                    :style="{ 'border': '2px solid #' + item.item.tags['Редкость'].color }">
                    <img src="@/assets/img/closegray.svg" class="delete" alt="" @click="deleteItem(item.id)">
                    <img :src="item.item.img" alt="">
                    <p>{{ item.item.name }}</p>
                    <div class="text-right">
                        <span>{{ item.item.sell_price.toFixed(1).toLocaleString() }} ₸</span>
                    </div>
                </div>
            </div>

            <div class="cart__complete">
                <span>КОЛИЧЕСТВО ТОВАРОВ: {{ cart.length }}</span>
                <span>иТОГО: {{ totalAmount }} ₸ </span>
                <button ref="purchases" @click="confirmPur()">Подтвердить заказ</button>
            </div>
        </div>
    </div>
</template>
<script>
import global from '~/mixins/global';
import axios from 'axios';
export default {
    mixins: [global],
    data() {
        return {
            pathUrl: 'https://dotashop.kz',
            cart: [],
        }
    },
    computed: {
        totalAmount() {
            return this.cart.reduce((total, item) => {
                return total + item.item.sell_price;
            }, 0).toFixed(1).toLocaleString();
        },
    },

    methods: {
        confirmPur() {
            const url = `${this.pathUrl}/api/products/confirm-busket`
            this.$refs.purchases.innerHTML = 'Покупаем'

            const token = this.getAuthorizationCookie();

            axios.defaults.headers.common['Authorization'] = `Token ${token}`;

            axios
                .get(url)
                .then((res) => {
                    console.log(res)
                    this.getCart()
                    this.$refs.purchases.innerHTML = 'Куплено'
                })
                .catch(error => {
                    console.error(error.message);
                    if (error.message == 'Request failed with status code 304') {
                        this.$refs.purchases.innerHTML = 'Недостаточно средств'
                    }
                });
        },
        deleteItem(id) {
            const url = `${this.pathUrl}/api/products/delete-busket-item/${id}`

            const token = this.getAuthorizationCookie();

            axios.defaults.headers.common['Authorization'] = `Token ${token}`;

            axios
                .get(url)
                .then((res) => {
                    this.getCart()
                })
        },
        getCart() {
            const url = `${this.pathUrl}/api/users/profile/`

            const token = this.getAuthorizationCookie();

            axios.defaults.headers.common['Authorization'] = `Token ${token}`;

            axios
                .get(url)
                .then((res) => {
                    this.balance = res.data.balance
                    this.cart = res.data.basket
                })
        },
    },
    mounted() {
        this.getCart()
    },
}
</script>
<script setup>
useSeoMeta({
    title: 'Подтверждение покупки | DotaShop',
    ogTitle: 'Подтверждение покупки | DotaShop',
    description: 'Подтверждение покупки | DotaShop',
    ogDescription: 'Подтверждение покупки | DotaShop',
})
</script>
<style lang="scss" scoped>
.page {
    padding: 73px 10.4vw 50px 200.006px;


    @media (max-width: 1600px) {
        padding: 73px 50px 50px 200px;
    }

    @media (max-width: 1024px) {
        padding: 140px 20px 50px;
    }

    .empty {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        border-radius: 10px;
        background: #292238;
        width: 100%;
        height: 460px;

        h2 {
            font-size: 20px;
            font-style: normal;
            font-weight: 500;
            line-height: 130%;
            /* 26px */
            letter-spacing: 1px;
            text-transform: uppercase;
            font-family: var(--mon);
            color: #fff;
            margin: 0 0 50px;
        }

        a {
            border-radius: 10px;
            border: 1px solid var(--iris-100, #5D5FEF);
            background: var(--iris-100, #5D5FEF);
            padding: 10px 20px;
            text-decoration: none;

            font-size: 16px;
            font-style: normal;
            font-weight: 400;
            line-height: 130%;
            font-family: var(--mon);
            color: #fff;
        }
    }

    .cart__body {
        margin-top: 30px;
        display: flex;
        align-items: flex-start;
        justify-content: space-between;
        gap: 60px;

        @media (max-width: 1024px) {
            flex-direction: column;
            gap: 20px;
        }

        .cart__complete {
            padding: 20px 20px 27px;
            border-radius: 10px;
            background: #292238;
            min-width: 345px;

            @media (max-width: 1024px) {
                width: 100%;
            }

            span {
                font-size: 20px;
                font-style: normal;
                font-weight: 500;
                line-height: 130%;
                display: block;
                /* 26px */
                letter-spacing: 1px;
                text-transform: uppercase;
                font-family: var(--mon);
                color: #fff;
                margin-bottom: 20px;

                @media (max-width: 1024px) {
                    font-size: 16px;
                }
            }

            button {
                margin-top: 5px;
                padding: 10px 20px;
                border-radius: 10px;
                border: 1px solid var(--iris-100, #5D5FEF);
                background: var(--iris-100, #5D5FEF);

                font-size: 16px;
                font-style: normal;
                font-weight: 400;
                line-height: 130%;
                font-family: var(--mon);
                color: #fff;
            }

        }

        .catalog__body {
            display: grid;
            gap: 30px;
            grid-auto-flow: dense;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            width: 100%;

            .catalog__item {
                text-decoration: none;
                display: flex;
                flex-direction: column;
                position: relative;
                gap: 10px;
                border-radius: 10px;
                background: linear-gradient(90deg, #24212B 0%, rgba(36, 33, 43, 0.65) 100%);
                padding: 10px;

                .delete {
                    position: absolute;
                    right: 5%;
                    top: 5%;
                    cursor: pointer;
                }

                p,
                span {
                    margin: 0;
                    font-size: 16px;
                    font-style: normal;
                    font-weight: 600;
                    line-height: 130%;
                    font-family: var(--mon);
                    color: #fff;
                }
            }

            .green {
                border: 2px solid #ADE55C;
            }

            .golden {
                border: 2px solid #E4AE39;
            }

            .blackblue {
                border: 2px solid #3348E0;
            }

            .whiteblue {
                border: 2px solid #458AD9;
            }

            .calblue {
                border: 2px solid #B0C3D9;
            }

            .purple {
                border: 2px solid #7047F2;
            }
        }
    }

    h1 {
        font-size: 32px;
        font-style: normal;
        font-weight: 400;
        line-height: 130%;
        /* 41.6px */
        letter-spacing: 1.6px;
        text-transform: uppercase;
        font-family: var(--col);
        color: #fff;
        margin: 27px 0 30px;
    }
}
</style>