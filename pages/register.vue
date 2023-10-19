<template>
    <div class="page">
        <div class="form">
            <div class="text-center">
                <img src="@/assets/img/reglogo.svg" class="img-fluid" alt="">
            </div>

            <h1 class="text-center">
                регистрация
            </h1>
            <div class="text-center">
                <small>Внимание! Если вы зарегистрируетесь через почту, функция продажи предметов будет недоступна.</small>
                <small>Зарегистрируйтесь через Steam для подключения своего инвентаря и доступа ко всем функциям!</small>

                <div class="d-flex justify-content-center">
                    <button class="steam" @click="loginSteam()">
                        <img src="@/assets/img/steam.svg" alt="">
                        <span>Войти через Steam</span>
                    </button>
                </div>
            </div>

            <div class="inputs">
                <div>
                    <label for="email">Ваш e-mail</label>
                    <input type="email" name="email" id="email" placeholder="E-mail" v-model="email">
                </div>
                <div>
                    <label for="password">пароль</label>
                    <div class="showpass">
                        <input :type="showPassword ? 'text' : 'password'" name="password" id="password"
                            placeholder="Введите пароль" v-model="password">
                        <img @click="togglePasswordVisibility('password-repeat')" src="@/assets/img/showpass.svg" alt=""
                            srcset="" />
                    </div>
                </div>
                <div>

                    <label for="password-repeat">повторите пароль</label>
                    <div class="showpass">
                        <input :type="showPassword ? 'text' : 'password'" name="password-repeat" id="password-repeat"
                            placeholder="Повторите пароль" v-model="repeat__password">
                        <img @click="togglePasswordVisibility('password-repeat')" src="@/assets/img/showpass.svg" alt=""
                            srcset="" />
                    </div>
                </div>

                <button @click="register()">Регистрация</button>

                <div class="text-center">
                    <span>Есть аккаунт? <NuxtLink to='/login'>Войти</NuxtLink></span>
                </div>
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
            showPassword: false,
            email: '',
            password: '',
            repeat__password: '',
        }
    },
    methods: {
        loginSteam() {
            const url = `${this.pathUrl}/api/users/login-steam/`

            const csrf = this.getCSRFToken()

            axios.defaults.headers.common['X-CSRFToken'] = csrf;

            axios
                .get(url)
                .then((res) => {
                    console.log(res)
                    window.location.href = res.data.url
                })
                .catch((error) => {
                    this.error = error.response.data.detail
                    console.log(error.response);
                });
        },
        register() {
            const url = `${this.pathUrl}/api/users/registration`
            const csrf = this.getCSRFToken()

            axios.defaults.headers.common['X-CSRFToken'] = csrf;
            axios
                .post(url, { first_name: this.email, password: this.password, username: this.email, email: this.email })
                .then((res) => {


                    console.log(res)
                    localStorage.setItem('accountType', 'email')
                    if (res.status == 202) {
                        document.cookie = `Authorization=${res.data.token}; expires=Fri, 31 Dec 2023 23:59:59 GMT; path=/`;
                        window.location.href = '/account'

                    }
                })
                .catch((error) => {
                    this.error = error.response.data.detail
                    console.log(error.response);
                });

        },
        togglePasswordVisibility(inputId) {
            const inputElement = document.getElementById(inputId);
            if (inputElement) {
                this.showPassword = !this.showPassword;
                inputElement.type = this.showPassword ? 'text' : 'password';
            }
        },
    },
    mounted() {
        const accType = localStorage.getItem('accountType')

        if (accType == 'steam' || accType == 'email') {
            this.$router.push('/account')

        }
        else {

        }
    }
}
</script>
<script setup>
useSeoMeta({
    title: 'Регистрация | DotaShop',
    ogTitle: 'Регистрация | DotaShop',
    description: 'Регистрация | DotaShop',
    ogDescription: 'Регистрация | DotaShop',
})
</script>
<style lang="scss" scoped>
.page {
    background: url('@/assets/img/reg.png') no-repeat;

    @media (max-width: 1024px) {
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 50px 20px 50px;
    }

    .form {
        height: 100vh;
        padding: 50px 54px 21px;
        max-width: 600px;

        @media (max-width: 1024px) {
            height: auto;
            max-width: 100%;
            padding: 30px 10px;
            border-radius: 10px;
        }

        border-radius: 0px 20px 20px 0px;
        background: rgba(66, 56, 86, 0.90);
        backdrop-filter: blur(2px);

        .showpass {
            position: relative;

            img {
                position: absolute;
                right: 3%;
                top: 25%;
                cursor: pointer;

                @media (max-width: 1024px) {
                    top: 20%;
                }
            }
        }

        .inputs {
            margin-top: 30px;
            padding: 0 20px;

            @media (max-width: 1024px) {
                padding: 0;
            }

            button {
                width: 100%;
                padding: 11.5px 0;
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

            span {
                margin-top: 20px;
                font-size: 16px;
                font-style: normal;
                font-weight: 400;
                line-height: normal;
                font-family: var(--mon);
                color: #fff;

                @media (max-width: 1024px) {
                    font-size: 12px;
                }

                a {
                    color: #fff;
                    text-decoration: underline;
                }
            }
        }

        input {
            width: 100%;
            margin-bottom: 30px;
            background: #0D0323;
            border: 0;
            border-radius: 0;
            padding: 14px 15px;

            font-size: 20px;
            font-style: normal;
            font-weight: 400;
            line-height: 24px;
            font-family: var(--mon);
            color: #fff;

            @media (max-width: 1024px) {
                margin-bottom: 20px;
                font-size: 16px;
                padding: 8px 15px;
            }
        }

        label {
            font-size: 24px;
            font-style: normal;
            font-weight: 400;
            line-height: 24px;
            /* 100% */
            letter-spacing: 1.2px;
            text-transform: uppercase;
            font-family: var(--col);
            color: #fff;
            margin: 0 0 10px;

            @media (max-width: 1024px) {
                font-size: 16px;
            }
        }

        label,
        input,
        span {
            display: block;
        }

        .steam {
            margin-top: 10px;
            display: flex;
            align-items: center;
            gap: 10px;
            padding: 11.5px 23px;
            border-radius: 10px;
            border: 1px solid var(--iris-100, #5D5FEF);
            background: #252654;

            font-size: 16px;
            font-style: normal;
            font-weight: 400;
            line-height: 130%;
            font-family: var(--mon);
            color: #fff;
        }

        h1 {
            margin: 80px 0 30px;
            font-size: 32px;
            font-style: normal;
            font-weight: 400;
            line-height: 130%;
            /* 41.6px */
            letter-spacing: 1.6px;
            text-transform: uppercase;

            font-family: var(--col);
            color: #fff;

            @media (max-width: 1024px) {
                margin: 23px 0 10px;
                font-size: 20px;
            }
        }

        small {
            text-align: center;
            display: block;
            font-size: 16px;
            font-style: normal;
            font-weight: 400;
            line-height: 130%;
            font-family: var(--mon);
            color: #fff;
            margin: 0 0 10px;

            @media (max-width: 1024px) {
                font-size: 12px;
            }
        }
    }
}
</style>