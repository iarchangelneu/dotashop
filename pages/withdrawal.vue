<template>
    <div class="page">
        <PrevPage></PrevPage>

        <div class="form">
            <div class="form__body">
                <h1 class="text-center">
                    ВЫВОД СРЕДСТВ
                </h1>

                <div class="type">
                    <NuxtLink to="/refill">Пополнить баланс</NuxtLink>
                    <NuxtLink to="/withdrawal">Вывести средства</NuxtLink>
                </div>
                <p>Вывод средств осуществляется только на подтвержденные карты, с которых было произведено пополнение.</p>
                <p>Процесс обработки заявки обычно занимает меньше часа, но может занять до 3-х рабочих дней.</p>

                <h2>Порядок действий для вывода средств</h2>

                <div class="paytype">
                    <p>1. Введите реквизиты карты:</p>
                </div>

                <div class="footer">
                    <p>2. Подтвердите Ваше согласие с правилами нашей системы</p>

                    <div>
                        <input type="radio" id="terms">
                        <label for="terms">Я согласен с <NuxtLink to="/terms"> пользовательским соглашением</NuxtLink>
                            и <NuxtLink to="/terms">политикой конфиденциальности</NuxtLink></label>
                    </div>

                    <div class="d-block">
                        <p class="mt-4">Укажите реквизиты вашей карты</p>
                        <div class="cardd">
                            <input type="text" class="mb-3 w-100" name="card" id="card" v-model="cardNumber"
                                :maxlength="cardNumberMaxLength" placeholder="Введите номер карты" @input="formatCardNumber"
                                autocomplete="cc-number">
                            <input type="text" class="mb-3 w-100" name="cardHolder" id="card" v-model="cardHolder"
                                placeholder="Введите владельца карты" autocomplete="cc-name">
                        </div>
                    </div>

                    <p class="mt-4">3. Введите сумму, которую Вы хотите вывести на свой счет</p>

                    <div class="pay">
                        <input type="number" v-model="cost">
                        <button ref="outBtn" @click="outMoney">Вывести</button>
                    </div>

                    <div class="select">
                        <button :class="{ active: cost == 100 }" @click="cost = 100">100 ₸</button>
                        <button :class="{ active: cost == 1000 }" @click="cost = 1000">1000 ₸</button>
                        <button :class="{ active: cost == 2000 }" @click="cost = 2000">2000 ₸</button>
                        <button :class="{ active: cost == 5000 }" @click="cost = 5000">5000 ₸</button>
                        <button :class="{ active: cost == 10000 }" @click="cost = 10000">10000 ₸</button>
                    </div>
                </div>
            </div>
        </div>
        <img src="@/assets/img/moneybg.png" class="bg" alt="">
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
            payType: '',
            cost: null,
            cardNumber: '',
            cardHolder: '',
            phone: '',
            cardNumberMaxLength: 19,
        }
    },
    methods: {
        outMoney() {
            const token = this.getAuthorizationCookie()
            const csrf = this.getCSRFToken()
            const path = `${this.pathUrl}/api/money/pay-return`
            axios.defaults.headers.common['Authorization'] = `Token ${token}`;
            axios.defaults.headers.common['X-CSRFToken'] = csrf;
            this.$refs.outBtn.innerHTML = 'Ожидайте'

            axios
                .post(path, {
                    amount: this.cost,
                    card_number: this.cardNumber.replace(/\s/g, ''),
                    cardholder: this.cardHolder
                })
                .then(response => {
                    console.log(response)
                    if (response.status == 200) {
                        this.$refs.outBtn.innerHTML = 'Успешно'
                    }
                    if (response.status == 228) {
                        if (response.data.error_msg == 'ov_merchant_balance_insufficient') {
                            this.$refs.outBtn.innerHTML = 'Недостаточно средств'
                        }
                        else {
                            this.$refs.outBtn.innerHTML = response.data.error_msg
                        }

                    }

                })
                .catch(error => {
                    console.error(error)
                    this.$refs.outBtn.innerHTML = 'ВЫВЕСТИ'
                })
        },
        formatCardNumber() {
            this.cardNumber = this.cardNumber.replace(/\D/g, '');
            this.cardNumber = this.cardNumber.replace(/(.{4})/g, '$1 ');
            this.cardNumber = this.cardNumber.slice(0, this.cardNumberMaxLength);
        }
    },
    watch: {
        cardNumber(newCardNumber) {
            this.cardHolder = this.cardNumberToHolderMapping[newCardNumber] || "";
        }
    },

}
</script>
<script setup>
useSeoMeta({
    title: 'Вывод средств | DotaShop',
    ogTitle: 'Вывод средств | DotaShop',
    description: 'Вывод средств | DotaShop',
    ogDescription: 'Вывод средств | DotaShop',
})
</script>
<style lang="scss" scoped>
.page {
    padding: 73px 0 0 200px;
    // height: 100%;
    position: relative;

    @media (max-width: 1024px) {
        padding: 150px 20px 50px;
    }

    .bg {
        position: absolute;
        // width: 743px;
        // height: 685px;
        right: 0;
        bottom: -1.5%;
        z-index: 1;

        @media (max-width: 1024px) {
            display: none;
        }

    }

    .form {
        z-index: 2;
        margin-top: 20px;
        padding-bottom: 140px;
        display: flex;
        justify-content: center;
        // max-width: 680px;
        position: relative;
        margin-right: 190px;

        @media (max-width: 1024px) {
            margin-right: 0;
            padding: 0;
        }

        .cardd {
            display: flex;
            flex-direction: column;

            input {
                display: block;
                border-radius: 10px;
                border: 2px solid #5D5FEF;
                padding: 12px 10px 10px;
                background: transparent;

                font-size: 20px;
                font-style: normal;
                font-weight: 700;
                line-height: normal;

                font-family: var(--mon);
                color: #fff;
            }
        }

        .select {
            margin-top: 20px;
            display: flex;
            justify-content: center;
            gap: 11.94px;
            flex-wrap: wrap;

            .active {
                background: #5D5FEF !important;
            }

            button {
                border-radius: 10px;
                border: 2px solid #5D5FEF;
                background: transparent;
                padding: 11px 18px;
                transition: all .3s ease;

                font-size: 20px;
                font-style: normal;
                font-weight: 700;
                line-height: normal;
                font-family: var(--mon);
                color: #fff;

                @media (max-width: 1024px) {
                    font-size: 16px;
                }
            }
        }

        .pay {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 20px;

            input {
                flex: 1;
                text-align: right;
                border-radius: 10px;
                border: 2px solid #5D5FEF;
                padding: 12px 10px 10px;
                background: transparent;

                font-size: 20px;
                font-style: normal;
                font-weight: 700;
                line-height: normal;

                font-family: var(--mon);
                color: #fff;
                max-width: 220px;

                @media (max-width: 1024px) {
                    max-width: 155px;
                }
            }

            button {
                flex: 1;
                max-width: 220px;
                padding: 10px 0;

                border-radius: 10px;
                border: 1px solid var(--iris-100, #5D5FEF);
                background: var(--iris-100, #5D5FEF);

                font-size: 20px;
                font-style: normal;
                font-weight: 400;
                line-height: 130%;
                font-family: var(--mon);
                color: #fff;

                @media (max-width: 1024px) {
                    max-width: 155px;
                }
            }
        }

        .footer {
            p {
                margin: 0 0 20px;
            }

            div {
                display: flex;
                gap: 10px;

                label {
                    margin: 0;
                    font-size: 16px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: normal;
                    font-family: var(--mon);
                    color: #fff;
                    max-width: 440px;

                    a {
                        color: #fff;
                        text-decoration: underline;
                    }
                }
            }
        }

        .paytype {
            p {
                margin-top: 0;
                margin-bottom: 20px;
            }

            div {
                display: flex;
                gap: 10px;
                margin-bottom: 20px;

                label {
                    font-size: 16px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: normal;
                    font-family: var(--mon);
                    color: #fff;
                    margin: 0;
                }
            }
        }

        h2 {
            margin: 30px 0 20px;
            font-size: 20px;
            font-style: normal;
            font-weight: 700;
            line-height: normal;
            font-family: var(--mon);
            color: #fff;

            @media (max-width: 1024px) {
                font-size: 16px;
                margin: 20px 0;
            }
        }

        p {
            max-width: 600px;
            font-size: 16px;
            font-style: normal;
            font-weight: 400;
            line-height: 130%;
            font-family: var(--mon);
            color: #fff;
            margin: 15px 0 0;
        }

        .type {
            margin-top: 25px;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 10px;

            a {
                text-decoration: none;
                text-align: center;
                flex: 1;
                padding: 10px 0;
                border-radius: 10px;
                background: #0D0323;

                font-size: 16px;
                font-style: normal;
                font-weight: 400;
                line-height: normal;
                font-family: var(--mon);
                color: #fff;

                @media (max-width: 1024px) {
                    font-size: 12px;
                }

                &:last-child {
                    border-radius: 10px;
                    background: #5D5FEF;
                }
            }
        }

        h1 {
            font-size: 32px;
            font-style: normal;
            font-weight: 400;
            line-height: normal;
            letter-spacing: 1.6px;
            font-family: var(--col);
            color: #fff;

            @media (max-width: 1024px) {
                font-size: 20px;
            }
        }

        .form__body {
            border-radius: 10px;
            background: #292238;
            padding: 44px 40px 48px;

            @media (max-width: 1024px) {
                padding: 20px 10px;
            }
        }
    }
}
</style>