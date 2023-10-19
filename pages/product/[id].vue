<template>
    <div class="page">
        <prevPage></prevPage>
        <div v-if="product.length <= 0"></div>
        <div class="item__body" v-else>
            <div class="image__block" :style="{ 'border': '2px solid #' + product.tags['Редкость'].color }">
                <img :src="product.img" class="img-fluid" alt="">
            </div>

            <div class="description">
                <div class="why">
                    <h1>{{ product.name }}</h1>

                    <span>Герой: {{ product.tags['Герой'].name }}</span>
                    <span>Редкость: <small :style="{ 'color': '#' + product.tags['Редкость'].color }">{{
                        product.tags['Редкость'].name }}</small></span>
                    <span :style="{ 'color': '#' + product.tags['Качество'].color }">Качество: {{
                        product.tags['Качество'].name }}</span>
                    <span>Слот: {{ product.tags['Ячейка'].name }}</span>

                    <div class="price">
                        <p>{{ product.sell_price.toFixed(1).toLocaleString() }} ₸</p>
                        <button ref="cart" @click="addCart">Купить</button>
                    </div>
                </div>
                <div class="desc" v-html="product.descriptions"></div>
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
            productId: this.$route.params.id,
            product: [],
            description: 'Жар решимости Дэвиона ненадолго сливает воедино элементы и материю',
            pathUrl: 'https://dotashop.kz',
            catalog: [],
        }
    },
    methods: {
        addCart() {
            const url = `${this.pathUrl}/api/products/add-busket-item/${this.productId}`
            const token = this.getAuthorizationCookie();

            this.$refs.cart.innerHTML = 'Добавляем'
            axios.defaults.headers.common['Authorization'] = `Token ${token}`;
            axios
                .get(url)
                .then((res) => {
                    console.log(res)

                    if (res.status == 201) {
                        this.$refs.cart.innerHTML = 'Добавлен'
                    }
                    else (
                        this.$refs.cart.innerHTML = 'Ошибка'
                    )
                })
                .catch((error) => {
                    console.log(error)
                })
        },
        getProduct() {
            const url = `${this.pathUrl}/api/products/get-detail-item/${this.productId}`
            axios
                .get(url)
                .then(response => {
                    this.product = response.data;
                })
                .catch(error => {
                    console.error(error);
                });
        },
    },
    mounted() {
        this.getProduct()
    },
}
</script>
<script setup>
useSeoMeta({
    title: 'Товар | DotaShop',
    ogTitle: 'Товар | DotaShop',
    description: 'Товар | DotaShop',
    ogDescription: 'Товар | DotaShop',
})
</script>
<style lang="scss" scoped>
.page {
    padding: 73px 50px 73px 10.417vw;

    @media (max-width: 1024px) {
        padding: 140px 20px 50px;
    }

    .item__body {
        display: flex;
        align-items: flex-start;
        gap: 30px;
        margin-top: 30px;

        @media (max-width: 1024px) {
            margin-top: 20px;
            gap: 20px;
            flex-direction: column;
            border-radius: 10px;
            background: #292238;
            padding: 10px;
        }

        .description {
            padding: 30px 26px 35px 30px;
            border-radius: 10px;
            background: #292238;
            display: flex;
            gap: 20px;
            align-items: flex-start;

            @media (max-width: 1024px) {
                padding: 0;
                flex-direction: column;
                gap: 20px;
            }

            .why {
                @media (max-width: 1024px) {
                    width: 100%;
                }
            }

            .desc {
                margin-top: 70px;
                font-size: 20px;
                font-style: normal;
                font-weight: 400;
                line-height: 130%;
                color: #fff;
                font-family: var(--mon);
                max-width: 640px;

                @media(max-width: 1024px) {
                    margin-top: 0;
                    font-size: 16px;
                }
            }

            .price {
                display: flex;
                gap: 30px;
                margin-top: 62px;

                @media (max-width: 1024px) {
                    margin-top: 20px;
                    gap: 20px;
                    width: 100%;
                }

                p {
                    font-size: 32px;
                    font-style: normal;
                    font-weight: 600;
                    line-height: 130%;
                    font-family: var(--mon);
                    color: #fff;
                    margin: 0;
                    white-space: nowrap;

                    @media (max-width: 1024px) {
                        flex: 1;
                    }
                }

                button {
                    padding: 10px 2.76vw;
                    border-radius: 10px;
                    border: 1px solid var(--iris-100, #5D5FEF);
                    background: var(--iris-100, #5D5FEF);

                    font-size: 20px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: 130%;
                    font-family: var(--mon);
                    color: #fff;
                    white-space: nowrap;

                    @media (max-width: 1024px) {
                        flex: 1;
                        padding: 10px 0;
                    }
                }
            }

            h1 {
                font-size: 36px;
                font-style: normal;
                font-weight: 600;
                line-height: 130%;
                font-family: var(--mon);
                color: #fff;
                margin: 0 0 20px;

                @media (max-width: 1024px) {
                    font-size: 20px;
                }
            }

            span {
                display: block;
                font-size: 20px;
                font-style: normal;
                font-weight: 500;
                line-height: 130%;
                font-family: var(--mon);
                color: #fff;
                margin: 0 0 10px;

                @media (max-width: 1024px) {
                    font-size: 16px;
                }

                &:last-child {
                    margin: 0;
                }

            }
        }

        .image__block {
            padding: 22px;
            border-radius: 10px;
            background: linear-gradient(90deg, #24212B 0%, rgba(36, 33, 43, 0.65) 100%);

            img {
                width: 26.302vw;
                object-fit: cover;
            }

            @media (max-width: 1024px) {
                width: 100%;


                img {
                    width: 100%;
                    height: 202px;
                }
            }
        }
    }
}
</style>