<template>
    <div class="page">
        <PrevPage></PrevPage>
        <h1>подтверждение покупки</h1>
        <!-- <div class="empty">
            <h2>Вы пока не добавили предметы в корзину</h2>
            <NuxtLink to="/catalog">Перейти в магазин</NuxtLink>
        </div> -->
        <div class="cart__body">
            <div class="catalog__body">
                <div class="catalog__item green">
                    <img src="@/assets/img/closegray.svg" class="delete" alt="">
                    <img src="@/assets/img/catalog1.png" alt="">
                    <p>Fiery Soul of the Slayer</p>
                    <div class="text-right">
                        <span>19 800 ₸</span>
                    </div>
                </div>
                <div class="catalog__item purple">
                    <img src="@/assets/img/closegray.svg" class="delete" alt="">
                    <img src="@/assets/img/catalog1.png" alt="">
                    <p>Fiery Soul of the Slayer</p>
                    <div class="text-right">
                        <span>19 800 ₸</span>
                    </div>
                </div>
                <div class="catalog__item calblue">
                    <img src="@/assets/img/closegray.svg" class="delete" alt="">
                    <img src="@/assets/img/catalog1.png" alt="">
                    <p>Fiery Soul of the Slayer</p>
                    <div class="text-right">
                        <span>19 800 ₸</span>
                    </div>
                </div>
                <div class="catalog__item whiteblue">
                    <img src="@/assets/img/closegray.svg" class="delete" alt="">
                    <img src="@/assets/img/catalog1.png" alt="">
                    <p>Fiery Soul of the Slayer</p>
                    <div class="text-right">
                        <span>19 800 ₸</span>
                    </div>
                </div>
                <div class="catalog__item whiteblue">
                    <img src="@/assets/img/closegray.svg" class="delete" alt="">
                    <img src="@/assets/img/catalog1.png" alt="">
                    <p>Fiery Soul of the Slayer</p>
                    <div class="text-right">
                        <span>19 800 ₸</span>
                    </div>
                </div>
            </div>

            <div class="cart__complete">
                <span>КОЛИЧЕСТВО ТОВАРОВ: 4</span>
                <span>иТОГО: 84 890 ₸ </span>
                <button>Подтвердить заказ</button>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {

        }
    }
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

        .cart__complete {
            padding: 20px 20px 27px;
            border-radius: 10px;
            background: #292238;
            min-width: 345px;

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