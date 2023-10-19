<template>
    <div class="modal fade" id="modalFirst" tabindex="-1" aria-labelledby="modalFirst" aria-hidden="true">
        <div class="modal-dialog modal-dialog-centered">
            <div class="modal-content">

                <div class="modal-body">
                    <h1>продать на dotashop</h1>

                    <div class="item__body">
                        <img :src="product.img" alt="">

                        <div>
                            <h2>{{ product.name }}</h2>

                            <span>
                                Ваша цена:
                            </span>

                            <div class="price">
                                <input type="number" v-model="cost">
                                <button @click="saleItem(product.name, product.id)">ПРОДАТЬ</button>
                            </div>
                            <small>{{ error }}</small>
                        </div>
                    </div>
                </div>

            </div>
        </div>
    </div>
    <ModalSecond :name="name"></ModalSecond>
</template>
<script>
import global from '~/mixins/global';
import axios from 'axios';
export default {
    mixins: [global],
    props: {
        product: Object,
    },
    data() {
        return {
            cost: null,
            error: '',
            pathUrl: 'https://dotashop.kz',
            name: '',
        }
    },
    methods: {
        saleItem(name, id) {
            const url = `${this.pathUrl}/api/products/sale-item/${id}/${this.cost}`
            const token = this.getAuthorizationCookie();
            this.name = name
            if (this.cost <= 0) {
                this.error = 'Сумма должна быть > 0'
            }
            else {
                axios.defaults.headers.common['Authorization'] = `Token ${token}`;

                axios
                    .get(url)
                    .then((res) => {
                        console.log(res)
                        if (res.status == 200) {
                            $('#modalFirst').modal('hide')
                            $('#modalSecond').modal('show')
                        }
                    })
                    .catch((error) => {
                        console.log(error)
                    })
            }
        },
    }
}
</script>

<style lang="scss" scoped>
.modal-body {
    padding: 0;

    .item__body {
        display: flex;
        align-items: flex-start;
        gap: 30px;

        @media (max-width: 1024px) {
            flex-direction: column;
            width: 100%;
        }

        img {
            max-width: 230px;

            @media (max-width: 1024px) {
                width: 100%;
                max-width: 97px;
            }
        }

        small {
            font-family: var(--mon);
            color: red;
            font-size: 14px;
            margin: 10px 0;
        }

        .price {
            display: flex;
            gap: 10px;
            align-items: center;

            input {
                border: 0;
                max-width: 145px;
                padding: 13px 10px;
                border-radius: 5px;
                background: #292238;

                font-size: 16px;
                font-style: normal;
                font-weight: 400;
                line-height: normal;
                font-family: var(--mon);
                color: #fff;

                @media (max-width: 1024px) {}
            }

            button {
                border-radius: 10px;
                border: 1px solid var(--iris-100, #5D5FEF);
                background: var(--iris-100, #5D5FEF);
                padding: 10px 20px;

                font-size: 16px;
                font-style: normal;
                font-weight: 400;
                line-height: 130%;
                font-family: var(--mon);
                color: #fff;
            }
        }

        span {
            font-size: 16px;
            font-style: normal;
            font-weight: 400;
            line-height: normal;
            font-family: var(--mon);
            color: #fff;
            margin: 0 0 10px;
            display: block;
        }

        h2 {
            font-size: 16px;
            font-style: normal;
            font-weight: 600;
            line-height: 130%;
            font-family: var(--mon);
            color: #fff;
            margin: 0 0 20px;
        }

    }

    h1 {
        font-size: 24px;
        font-style: normal;
        font-weight: 400;
        line-height: 130%;
        /* 31.2px */
        letter-spacing: 1.2px;
        text-transform: uppercase;
        font-family: var(--col);
        color: #fff;
        margin: 0 0 20px;

        @media (max-width: 1024px) {
            font-size: 16px;
        }
    }
}

.modal-content {
    border-radius: 10px;
    background: var(--Bg2, #160E21);
    box-shadow: 0px 4px 16px 0px rgba(86, 31, 140, 0.30);
    padding: 20px 30px 30px;
    border: 0;
}

@media (min-width: 576px) {
    .modal-dialog {
        max-width: 596px;
        margin: 1.75rem auto;
    }
}

@media (max-width: 1024px) {
    .modal-dialog {
        max-width: 350px;
        margin: 1.75rem auto;
    }
}
</style>