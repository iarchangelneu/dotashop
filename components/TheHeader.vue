<template>
    <header v-if="!hideHeaderOnPages.includes($route.name)">
        <div class="header__body">
            <div class="sidebar">
                <div class="sidebar__body" :class="{ navActive: sideActive }" @click="stopPropagation">
                    <div class="link">
                        <NuxtLink to="/">
                            <img src="@/assets/img/headerlogo.svg" alt="">
                        </NuxtLink>
                        <NuxtLink to="/" style="text-decoration: none;">
                            <h1 class="mb-0" :class="{ inactive: !sideActive }">DotaShop</h1>
                        </NuxtLink>
                        <img src="@/assets/img/burger2.svg" class="closeh" @click.stop="toggleMenu" alt="">
                    </div>
                    <NuxtLink to="/" class="navik">
                        <img src="@/assets/img/h1.svg" :class="{ activeimg: $route.path === '/' }" alt="">
                        <span :class="{ inactive: !sideActive, activeSpan: $route.path === '/' }">Главная</span>
                    </NuxtLink>
                    <a href="/#faq" class="navik">
                        <img :class="{ activeimg: $route.path === '/#faq' }" src="@/assets/img/h2.svg"
                            style="min-width: 50px; height: 50px;" alt="">
                        <span :class="{ inactive: !sideActive, activeSpan: $route.path === '/#faq' }">FAQ</span>
                    </a>
                    <NuxtLink to="/catalog" class="navik">
                        <img :class="{ activeimg: $route.path === '/catalog' }" src="@/assets/img/h3.svg" alt="">
                        <span :class="{ inactive: !sideActive, activeSpan: $route.path === '/catalog' }">Магазин</span>
                    </NuxtLink>
                    <NuxtLink to="/sale" class="navik">
                        <img :class="{ activeimg: $route.path === '/sale' }" src="@/assets/img/h4.svg" alt="">
                        <span :class="{ inactive: !sideActive, activeSpan: $route.path === '/sale' }">продажа</span>
                    </NuxtLink>
                </div>
                <img src="@/assets/img/burger.svg" v-if="!sideActive" class="open" @click.stop="toggleMenu" alt="">
            </div>
            <div class="acc__info">
                <div class="acc__body" v-if="isAuth">
                    <NuxtLink to="/withdrawal" class="cash">
                        <img src="@/assets/img/cash.svg" alt="">
                        <span v-if="balance !== null">{{ balance == null ? '0 ₸' :
                            balance.toFixed(1).toLocaleString()
                            + ' ₸' }}</span>
                    </NuxtLink>

                    <img src="@/assets/img/cart.svg" style="cursor: pointer;" @click.stop="toggleCart" alt="">

                    <NuxtLink to="/account" class="user">
                        <img src="@/assets/img/avatar.svg" alt="">
                        <span>личный кабинет</span>
                    </NuxtLink>
                </div>
                <div class="acc__body" v-else>


                    <NuxtLink to="/register" class="user">
                        <span>Вход/Регистрация</span>
                    </NuxtLink>
                </div>
            </div>
        </div>
        <div class="headermob">
            <NuxtLink to="/">
                <img src="@/assets/img/headermob.svg" class="img-fluid" alt="">
            </NuxtLink>
            <div class="yas">
                <img v-if="isAuth" src="@/assets/img/cart.svg" style="cursor: pointer;" @click.stop="toggleCart" alt="">
                <NuxtLink v-if="isAuth" to="/account" class="user">
                    <img src="@/assets/img/avatar.svg" alt="">
                </NuxtLink>
                <div class="burg">
                    <input id="menu__toggle" class="d-none" type="checkbox" />
                    <label class="menu__btn" for="menu__toggle" @click="menuOpen = !menuOpen">
                        <span></span>
                    </label>
                </div>
            </div>

            <div class="mobmenu" :class="{ activeMenu: menuOpen }">
                <div>
                    <NuxtLink to="/withdrawal" class="cashik">
                        <img src="@/assets/img/cash.svg" alt="" v-if="isAuth">
                        <span v-if="balance !== null">{{ balance == null ? '0 ₸' :
                            balance.toFixed(1).toLocaleString()
                            + ' ₸' }}</span>
                    </NuxtLink>

                    <NuxtLink to="/" class="navik">
                        <img src="@/assets/img/h1.svg" :class="{ activeimg: $route.path === '/' }" alt="">
                        <span :class="{ inactive: !sideActive, activeSpan: $route.path === '/' }">Главная</span>
                    </NuxtLink>
                    <a href="/#faq" class="navik">
                        <img :class="{ activeimg: $route.path === '/#faq' }" src="@/assets/img/h2.svg"
                            style="min-width: 50px; height: 50px;" alt="">
                        <span :class="{ inactive: !sideActive, activeSpan: $route.path === '/#faq' }">FAQ</span>
                    </a>
                    <NuxtLink to="/catalog" class="navik">
                        <img :class="{ activeimg: $route.path === '/catalog' }" src="@/assets/img/h3.svg" alt="">
                        <span :class="{ inactive: !sideActive, activeSpan: $route.path === '/catalog' }">Магазин</span>
                    </NuxtLink>
                    <NuxtLink to="/sale" class="navik">
                        <img :class="{ activeimg: $route.path === '/sale' }" src="@/assets/img/h4.svg" alt="">
                        <span :class="{ inactive: !sideActive, activeSpan: $route.path === '/sale' }">продажа</span>
                    </NuxtLink>
                </div>
            </div>
        </div>
    </header>
    <div class="cart" :class="{ cartOpen: cartOpen }" @click="stopPropagation">
        <img src="@/assets/img/close.svg" @click="closeCart" style="cursor: pointer;" alt="">

        <div class="cart__body">
            <div class="cart__item" v-for="item in cart" :key="cart.id">
                <div class="img" :style="{ 'border': '2px solid #' + item.item.tags['Редкость'].color }">
                    <img :src="item.item.img" alt="">
                </div>

                <div class="w-100">
                    <div class="delete">
                        <h2>{{ item.item.name }}</h2>
                        <img src="@/assets/img/close.svg" style="cursor: pointer;" @click="deleteItem(item.id)">
                    </div>

                    <span>{{ item.item.sell_price.toFixed(1).toLocaleString() }} ₸</span>
                </div>
            </div>
        </div>
        <hr>

        <div class="cart__footer">
            <p>иТОГО: {{ totalAmount }} ₸ </p>

            <div class="btns">
                <button ref="purchase" @click="confirmPur()">
                    Оформить заказ
                </button>
                <NuxtLink to="/cart">
                    Перейти в корзину
                </NuxtLink>
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
            sideActive: false,
            cartOpen: false,
            hideHeaderOnPages: ['login', 'register'],
            menuOpen: false,
            pathUrl: 'https://dotashop.kz',
            cart: [],
            balance: null,
            isAuth: false,
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
        calculateTotal() {
            let total = 0;

            this.cart.forEach(item => {
                const price = item.products;
                const discountedPrice = price;
                total += discountedPrice * item.amount;
            });

            return total;
        },
        confirmPur() {
            const url = `${this.pathUrl}/api/products/confirm-busket`
            this.$refs.purchase.innerHTML = 'Покупаем'

            const token = this.getAuthorizationCookie();

            axios.defaults.headers.common['Authorization'] = `Token ${token}`;

            axios
                .get(url)
                .then((res) => {
                    console.log(res)
                    this.getCart()
                    this.$refs.purchase.innerHTML = 'Куплено'
                })
                .catch(error => {
                    console.error(error);
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
        toggleMenu() {
            this.sideActive = !this.sideActive

            if (this.sideActive) {
                document.addEventListener('click', this.closeMenu);
            } else {
                document.removeEventListener('click', this.closeMenu);
            }
        },
        closeMenu() {
            this.sideActive = false;
            document.removeEventListener('click', this.closeMenu);
        },
        toggleCart() {
            this.cartOpen = !this.cartOpen;
            if (this.cartOpen) {
                document.addEventListener('click', this.closeCart);
                this.getCart()
            } else {
                document.removeEventListener('click', this.closeCart);
            }
        },
        closeCart() {
            this.cartOpen = false;
            document.removeEventListener('click', this.closeCart);
        },
        stopPropagation(event) {
            event.stopPropagation();
        },
    },
    mounted() {
        const accType = localStorage.getItem('accountType')

        if (accType == 'steam' || accType == 'email') {
            this.getCart()
            this.isAuth = true
        }
        else {

        }

    }
}
</script>
<style lang="scss" scoped>
.cartOpen {
    right: 0 !important;
}

.cart {
    width: 600px;
    height: 100vh;
    position: fixed;
    right: -3000px;
    z-index: 250;
    background: rgba(66, 56, 86, 0.90);
    backdrop-filter: blur(2px);
    transition: all .3s ease;
    padding: 99px 85px 50px 35px;

    @media (max-width: 1024px) {
        width: 100%;
        padding: 30px 30px;
    }

    hr {
        border-top: 2px solid #292238;
    }

    .cart__footer {
        p {
            font-size: 20px;
            font-style: normal;
            font-weight: 500;
            line-height: 130%;
            /* 26px */
            letter-spacing: 1px;
            text-transform: uppercase;
            margin: 0 0 20px;
            color: #fff;
            font-family: var(--mon);
        }

        .btns {
            display: flex;
            gap: 36px;

            @media (max-width: 1024px) {
                gap: 20px;
            }

            button,
            a {
                border-radius: 10px;
                border: 1px solid var(--iris-100, #5D5FEF);
                background: var(--iris-100, #5D5FEF);
                flex: 1;
                text-decoration: none;
                text-align: center;

                font-size: 16px;
                font-style: normal;
                font-weight: 400;
                line-height: 130%;
                font-family: var(--mon);
                color: #fff;
                padding: 10px 0;
                transition: all .3s ease;

                @media (max-width: 1024px) {
                    font-size: 14px;
                }

                &:hover {
                    border: 1px solid var(--iris-100, #5D5FEF);
                    background: #252654;
                }

                &:last-child {
                    border-radius: 10px;
                    border: 1px solid var(--iris-100, #5D5FEF);
                    background: #252654;

                    &:hover {
                        border: 1px solid var(--iris-100, #5D5FEF);
                        background: var(--iris-100, #5D5FEF);
                    }
                }
            }
        }
    }

    .cart__body {
        display: flex;
        flex-direction: column;
        gap: 30px;
        margin-top: 40px;
        width: 100%;
        height: 500px;
        overflow-y: auto;

        .cart__item {
            display: flex;
            gap: 20px;
            align-items: flex-start;
            width: 100%;

            .delete {
                display: flex;
                justify-content: space-between;
                align-items: flex-start;
                width: 100%;
            }

            h2 {
                font-size: 20px;
                font-style: normal;
                font-weight: 600;
                line-height: 130%;
                font-family: var(--mon);
                color: #fff;
                margin: 0;

                @media (max-width: 1024px) {
                    font-size: 14px;
                }
            }

            span {
                font-size: 20px;
                font-style: normal;
                font-weight: 700;
                line-height: 130%;
                font-family: var(--mon);
                color: #fff;

                @media (max-width: 1024px) {
                    font-size: 14px;
                }
            }

            .img {
                border-radius: 5px;

                img {
                    border-radius: 5px;
                    width: 150px;
                    height: 100px;
                    object-fit: cover;
                }
            }
        }
    }
}

header {
    position: fixed;
    width: 100%;
    z-index: 100;

    .headermob {
        display: none;

        .activeMenu {
            right: 0 !important;
        }

        .mobmenu {
            position: fixed;
            width: 100vw;
            right: -3000px;
            transition: all .3s ease;
            top: 0;
            height: 100vh;
            background: #160E21;
            display: flex;
            flex-direction: column;
            // justify-content: center;
            align-items: center;

            .navik {
                text-decoration: none;
                display: flex;
                width: 100%;
                margin-bottom: 20px;

                .activeimg {
                    border-radius: 10px;
                    background: rgba(217, 217, 217, 0.30);

                }

                .activeSpan {
                    border-radius: 10px;
                    background: rgba(255, 255, 255, 0.20);
                    margin-left: -49px;
                    padding: 16px 38px 14px 70px;
                    width: 100%;
                }

                img {
                    padding: 13px;
                    transition: all .3s ease;
                }

                span {
                    padding: 16px 38px 14px 20px;
                    font-size: 16px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: normal;
                    text-transform: uppercase;
                    transition: all .3s ease;

                    font-family: var(--mon);
                    color: #fff;
                }
            }

            .cashik {
                margin-bottom: 99px;
                margin-top: 171px;
                display: flex;
                gap: 5px;

                span {
                    font-size: 24px;
                    font-style: normal;
                    font-weight: 500;
                    line-height: normal;
                    font-family: var(--mon);
                    color: #fff;
                }
            }
        }

        @media (max-width: 1024px) {
            position: relative;
            display: flex;
            justify-content: space-between;
            gap: 25px;
            align-items: center;
            padding: 40px 20px 20px;
            border-radius: 0px 0 20px 20px;
            background: rgba(66, 56, 86, 0.50);
            backdrop-filter: blur(2px);
            width: 100%;
        }

        .yas {
            display: flex;
            gap: 25px;
            align-items: center;
        }
    }

    .header__body {
        position: relative;
        display: flex;
        justify-content: space-between;
        align-items: flex-start;

        @media (max-width: 1024px) {
            display: none;
        }
    }

    .acc__info {
        position: fixed;
        right: 0;
        padding: 40px 20px 0 0;

        .acc__body {
            padding: 20px;
            border-radius: 20px;
            background: rgba(66, 56, 86, 0.50);
            backdrop-filter: blur(2px);
            display: flex;
            align-items: center;
            gap: 30px;

            .user {
                display: flex;
                gap: 20px;
                align-items: center;
                text-decoration: none;

                span {
                    font-size: 20px;
                    font-style: normal;
                    font-weight: 500;
                    line-height: normal;
                    text-transform: uppercase;
                    font-family: var(--mon);
                    color: #fff;
                }
            }

            .cash {
                display: flex;
                gap: 5px;
                align-items: center;
                text-decoration: none;

                span {
                    font-size: 24px;
                    font-style: normal;
                    font-weight: 500;
                    line-height: normal;
                    font-family: var(--mon);
                    color: #fff;
                }
            }
        }
    }

    .sidebar {
        position: fixed;
        display: flex;
        align-items: flex-start;
        height: 100vh;
        padding: 20px 0;

        .inactive {
            opacity: 0 !important;
        }

        .navik {
            text-decoration: none;
            display: flex;
            width: 100%;

            .activeimg {
                border-radius: 10px;
                background: rgba(217, 217, 217, 0.30);

            }

            .activeSpan {
                border-radius: 10px;
                background: rgba(255, 255, 255, 0.20);
                margin-left: -49px;
                padding: 16px 38px 14px 70px;
                width: 100%;
            }

            img {
                padding: 13px;
                transition: all .3s ease;
            }

            span {
                padding: 16px 38px 14px 20px;
                font-size: 16px;
                font-style: normal;
                font-weight: 400;
                line-height: normal;
                text-transform: uppercase;
                transition: all .3s ease;

                font-family: var(--mon);
                color: #fff;
            }
        }

        .openLeft {
            left: 247px !important;
        }

        .closeh {
            margin-left: 30px;
            cursor: pointer;
        }

        .open {
            position: absolute;
            top: 73px;
            left: 120px;
            cursor: pointer;
            transition: all .3s ease;
        }

        .navActive {
            width: 294px !important;
            transition: all .3s ease;
        }

        .sidebar__body {
            border-radius: 0px 20px 20px 0px;
            height: 100%;
            width: 100px;
            transition: all .3s ease;
            background: rgba(66, 56, 86, 0.50);
            backdrop-filter: blur(2px);
            padding: 40px 30px;
            overflow: hidden;

            display: flex;
            flex-direction: column;
            gap: 34px;

            .link {
                display: flex;
                gap: 5px;
                align-items: center;

                h1 {
                    font-size: 24px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: normal;
                    font-family: var(--kha);
                    margin: 0;
                    color: #fff;
                    transition: all .3s ease;
                }
            }
        }
    }
}

#menu__toggle {
    opacity: 0;
}

.menu__btn {
    margin-top: 10px;
    display: flex;
    /* используем flex для центрирования содержимого */
    align-items: center;
    /* центрируем содержимое кнопки */
    width: 35px;
    height: 20px;
    cursor: pointer;
    z-index: 100000000;
    color: #fff;
    position: relative;
    transform: rotate(180deg);
}

.menu__btn>span {
    display: block;
    position: absolute;
    width: 100%;
    height: 2px;
    background-color: #fff;
}

.menu__btn>span::before,
.menu__btn>span::after {
    display: block;
    position: absolute;
    width: 100%;
    height: 2px;
    background-color: #fff;
}

.menu__btn>span::before {
    content: '';
    top: -8px;
}

.menu__btn>span::after {
    content: '';
    top: 8px;
}

#menu__toggle:checked~.menu__btn>span {
    transform: rotate(45deg);
    background-color: #fff;
    border-radius: 10px;

}

#menu__toggle:checked~.menu__btn>span::before {
    top: 0;
    transform: rotate(0);
    background-color: #fff;
    border-radius: 10px;

}

#menu__toggle:checked~.menu__btn>span::after {
    top: 0;
    transform: rotate(90deg);
    background-color: #fff;
    border-radius: 10px;
}

#menu__toggle:checked~.menu__box {
    visibility: visible;
    top: 0;
}

.menu__btn>span,
.menu__btn>span::before,
.menu__btn>span::after {
    transition-duration: .25s;
}
</style>