<template>
    <div class="page">
        <div class="form">
            <div class="text-center">
                <img src="@/assets/img/reglogo.svg" class="img-fluid" alt="">
            </div>

            <h1 class="text-center">
                Авторизация
            </h1>


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
                        <img @click="togglePasswordVisibility('password')" src="@/assets/img/showpass.svg" alt=""
                            srcset="" />
                    </div>
                </div>
                <small>{{ error }}</small>
                <div class="btns">
                    <button @click="login()">Войти</button>
                    <button class="steam" @click="loginSteam()">
                        <img src="@/assets/img/steam.svg" alt="">
                        <span>Войти через Steam</span>
                    </button>
                </div>


                <div class="text-center">
                    <span>Нет аккаунта? <NuxtLink to='/register'>Зарегистрироваться</NuxtLink></span>
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
            error: '',
        }
    },
    methods: {
        login() {
            const url = `${this.pathUrl}/api/users/authorization`

            const csrf = this.getCSRFToken()

            axios.defaults.headers.common['X-CSRFToken'] = csrf;

            axios
                .post(url, { username: this.email, password: this.password })
                .then((res) => {



                    document.cookie = `Authorization=${res.data.token}; expires=Fri, 31 Dec 2023 23:59:59 GMT; path=/`;
                    localStorage.setItem('accountType', 'email')

                    window.location.href = '/account'


                    console.log(res)
                })
                .catch((error) => {
                    console.log(error);
                    this.error = error.response.data.non_field_errors.toString()
                });
        },
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
    title: 'Авторизация | DotaShop',
    ogTitle: 'Авторизация | DotaShop',
    description: 'Авторизация | DotaShop',
    ogDescription: 'Авторизация | DotaShop',
})
</script>
<style lang="scss" scoped>
.page {
    background: url('@/assets/img/reg.png');

    @media (max-width: 1024px) {
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 50px 20px 50px;
    }

    small {
        color: red;
        font-family: var(--mon);
        font-size: 14px;
    }

    .form {
        height: 100vh;
        padding: 50px 54px 0;
        max-width: 600px;

        border-radius: 0px 20px 20px 0px;
        background: rgba(66, 56, 86, 0.90);
        backdrop-filter: blur(2px);

        @media (max-width: 1024px) {
            height: auto;
            max-width: 100%;
            padding: 30px 10px;
            border-radius: 10px;
        }

        .btns {
            display: flex;
            gap: 20px;
            align-items: flex-start;

            @media (max-width: 1024px) {
                flex-direction: column;
            }

            button {
                @media (max-width: 1024px) {
                    flex: 1;
                    width: 100%;
                    text-align: center;
                }
            }
        }

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
                padding: 11.5px 3.099vw;
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
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            padding: 10px 22px !important;
            border-radius: 10px;
            border: 1px solid var(--iris-100, #5D5FEF);
            background: #252654;

            span {
                margin: 0;
                font-size: 16px;
                font-style: normal;
                font-weight: 400;
                line-height: 130%;
                font-family: var(--mon);
                color: #fff;
            }
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