<template>
    <footer v-if="!hideFooterOnPages.includes($route.name)">
        <hr>
        <div class="footer__body">
            <img src="@/assets/img/footerlogo.svg" alt="">

            <div>
                <div class="links">
                    <div>
                        <NuxtLink to="/catalog">Магазин</NuxtLink>
                        <NuxtLink to="/sale">продажа</NuxtLink>
                    </div>
                    <div>
                        <a href="/#faq">FAQ</a>
                        <a href="/#sales">акции</a>
                    </div>
                    <div>
                        <NuxtLink to="/polytics">Политика конфиденциальности</NuxtLink>
                        <NuxtLink to="/terms">Пользовательское соглашение</NuxtLink>
                    </div>
                </div>
                <div class="copyright">
                    <small>г. Алматы, пр-кт Республики 13, Почтовый индекс A15X3C5 (050013), +7 775 816 82 48, БИН
                        210840016943<br>
                        Почта поддержки : support@casedota.kz</small>
                    <small>2023©casedota.kz </small>
                </div>
            </div>
        </div>
    </footer>
</template>
<script>
export default {
    data() {
        return {
            hideFooterOnPages: ['login', 'register'],
        }
    }
}
</script>
<style lang="scss" scoped>
footer {
    padding: 0 10.417vw 50px;

    @media (max-width: 1600px) {
        padding: 0 50px 50px 10.417vw;
    }

    @media (max-width: 1024px) {
        padding: 0 20px 40px;
    }

    img {
        @media (max-width: 1400px) {
            max-width: 20%;
        }

        @media (max-width: 1024px) {
            max-width: 100%;
        }
    }

    .footer__body {
        margin-top: 50px;
        display: flex;
        align-items: flex-start;
        gap: 6.458vw;

        @media (max-width: 1600px) {
            gap: 50px;
        }

        @media (max-width: 1024px) {
            flex-direction: column;
            gap: 30px;
        }
    }

    .copyright {
        display: flex;
        gap: 20px;
        margin-top: 39px;

        @media (max-width: 1024px) {
            flex-direction: column;
            gap: 10px;
            margin-top: 20px;
        }

        small {
            font-size: 16px;
            font-style: normal;
            font-weight: 400;
            line-height: 130%;
            font-family: var(--mon);
            color: #C8C8C8;
        }
    }

    .links {
        display: flex;
        gap: 6.979vw;

        @media (max-width: 1600px) {
            gap: 50px;
        }

        @media (max-width: 1024px) {
            gap: 30px;
            flex-wrap: wrap;
        }

        @media (max-width: 380px) {
            flex-direction: column;
        }

        div {
            display: flex;
            flex-direction: column;
            gap: 29px;

            a {
                font-size: 24px;
                font-style: normal;
                font-weight: 500;
                line-height: normal;
                text-transform: uppercase;
                font-family: var(--mon);
                color: #fff;
                text-decoration: none;

                @media (max-width: 1600px) {
                    font-size: 20px;

                }

                @media (max-width: 1024px) {
                    font-size: 16px;

                }

                @media (max-width: 380px) {
                    font-size: 14px;
                }

            }
        }
    }

    hr {
        margin-top: 0;
        border-top: 2px solid #fff;
    }
}
</style>