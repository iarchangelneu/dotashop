<template>
    <header>
        <div class="sidebar">
            <div class="sidebar__body" :class="{ navActive: sideActive }">
                <div class="link">
                    <img src="@/assets/img/headerlogo.svg" alt="">
                    <h1 :class="{ inactive: !sideActive }">DotaShop</h1>
                    <img src="@/assets/img/burger2.svg" class="closeh" @click="sideActive = !sideActive" alt="">
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
            <img src="@/assets/img/burger.svg" v-if="!sideActive" class="open" @click="sideActive = !sideActive" alt="">
        </div>
        <div class="acc__info">
            <div class="acc__body">
                <NuxtLink to="/withdrawal" class="cash">
                    <img src="@/assets/img/cash.svg" alt="">
                    <span>1000 ₸</span>
                </NuxtLink>

                <img src="@/assets/img/cart.svg" alt="">

                <NuxtLink to="/account" class="user">
                    <img src="@/assets/img/avatar.svg" alt="">
                    <span>личный кабинет</span>
                </NuxtLink>
            </div>
        </div>
    </header>
</template>
<script>
export default {
    data() {
        return {
            sideActive: false,
        }
    }
}
</script>
<style lang="scss" scoped>
header {
    position: relative;
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    z-index: 100;

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
</style>