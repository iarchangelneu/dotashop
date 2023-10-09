<template>
    <div class="page">
        <div class="main">
            <img src="@/assets/img/mainbg.png" alt="" class="bg">
            <div class="rotating-text d-flex justify-content-center w-100">
                <h1 class="rotating-text-pre">Хочешь скины на </h1>
                <h1 class="rotating-text-suf">
                    <span class="word" v-for="(word, wordIndex) in words" :key="wordIndex" :class="word.class">
                        <span class="letter" v-for="(letter, letterIndex) in word.letters" :key="letterIndex"
                            :class="letter.class" :style="{ opacity: letter.opacity }">{{ letter.char }}</span>
                    </span>
                </h1>
            </div>

            <div class="cards">
                <NuxtLink to="/catalog" alt="Mythrill" target="_blank">
                    <div class="cardd">
                        <div class="wrapper">
                            <img src="@/assets/img/cover1.jpg" class="cover-image" />
                        </div>
                        <img src="@/assets/img/text1.png" class="title" />
                        <img src="@/assets/img/character1.png" class="character" />
                    </div>
                </NuxtLink>
                <NuxtLink to="/catalog" alt="Mythrill" target="_blank">
                    <div class="cardd">
                        <div class="wrapper">
                            <img src="@/assets/img/cover1.jpg" class="cover-image" />
                        </div>
                        <img src="@/assets/img/text1.png" class="title" />
                        <img src="@/assets/img/character1.png" class="character" />
                    </div>
                </NuxtLink>
                <NuxtLink to="/catalog" alt="Mythrill" target="_blank">
                    <div class="cardd">
                        <div class="wrapper">
                            <img src="@/assets/img/cover1.jpg" class="cover-image" />
                        </div>
                        <img src="@/assets/img/text1.png" class="title" />
                        <img src="@/assets/img/character1.png" class="character" />
                    </div>
                </NuxtLink>
                <NuxtLink to="/catalog" alt="Mythrill" target="_blank">
                    <div class="cardd">
                        <div class="wrapper">
                            <img src="@/assets/img/cover1.jpg" class="cover-image" />
                        </div>
                        <img src="@/assets/img/text1.png" class="title" />
                        <img src="@/assets/img/character1.png" class="character" />
                    </div>
                </NuxtLink>
            </div>

            <div class="links text-center">
                <p>Переходи в наш каталог и одень своих персонажей или продай нам свои предметы</p>

                <div class="buttons">
                    <NuxtLink to="/catalog">Магазин</NuxtLink>
                    <NuxtLink to="/sale">Продажа</NuxtLink>
                </div>
            </div>
        </div>

        <a name="sales"></a>
        <div class="sales">
            <h1>Акции и скидки</h1>
            <p>Приобретайте товары по выгодным ценам</p>

            <div class="sales__slider">
                <swiper :slides-per-view="6" :space-between="30" :navigation="navigation" :breakpoints="breakpoints"
                    :modules="modules">
                    <swiper-slide>
                        <NuxtLink to="/product/1" class="slide green">
                            <div class="image">
                                <img src="@/assets/img/sale1.png" alt="">
                            </div>

                            <h2>Fiery Soul of the Slayer</h2>

                            <div class="price">
                                <small>
                                    22 800 ₸
                                    <img src="@/assets/img/discount.svg" alt="">
                                </small>
                                <p>19 800 ₸</p>
                            </div>
                        </NuxtLink>
                    </swiper-slide>
                    <swiper-slide>
                        <NuxtLink to="/product/1" class="slide golden">
                            <div class="image">
                                <img src="@/assets/img/sale2.png" alt="">
                            </div>

                            <h2>Fiery Soul of the Slayer</h2>

                            <div class="price">
                                <small>
                                    22 800 ₸
                                    <img src="@/assets/img/discount.svg" alt="">
                                </small>
                                <p>19 800 ₸</p>
                            </div>
                        </NuxtLink>
                    </swiper-slide>
                    <swiper-slide>
                        <NuxtLink to="/product/1" class="slide blackblue">
                            <div class="image">
                                <img src="@/assets/img/sale3.png" alt="">
                            </div>

                            <h2>Fiery Soul of the Slayer</h2>

                            <div class="price">
                                <small>
                                    22 800 ₸
                                    <img src="@/assets/img/discount.svg" alt="">
                                </small>
                                <p>19 800 ₸</p>
                            </div>
                        </NuxtLink>
                    </swiper-slide>
                    <swiper-slide>
                        <NuxtLink to="/product/1" class="slide whiteblue">
                            <div class="image">
                                <img src="@/assets/img/sale4.png" alt="">
                            </div>

                            <h2>Fiery Soul of the Slayer</h2>

                            <div class="price">
                                <small>
                                    22 800 ₸
                                    <img src="@/assets/img/discount.svg" alt="">
                                </small>
                                <p>19 800 ₸</p>
                            </div>
                        </NuxtLink>
                    </swiper-slide>
                    <swiper-slide>
                        <NuxtLink to="/product/1" class="slide calblue">
                            <div class="image">
                                <img src="@/assets/img/sale5.png" alt="">
                            </div>

                            <h2>Fiery Soul of the Slayer</h2>

                            <div class="price">
                                <small>
                                    22 800 ₸
                                    <img src="@/assets/img/discount.svg" alt="">
                                </small>
                                <p>19 800 ₸</p>
                            </div>
                        </NuxtLink>
                    </swiper-slide>
                    <swiper-slide>
                        <NuxtLink to="/product/1" class="slide purple">
                            <div class="image">
                                <img src="@/assets/img/sale6.png" alt="">
                            </div>

                            <h2>Fiery Soul of the Slayer</h2>

                            <div class="price">
                                <small>
                                    22 800 ₸
                                    <img src="@/assets/img/discount.svg" alt="">
                                </small>
                                <p>19 800 ₸</p>
                            </div>
                        </NuxtLink>
                    </swiper-slide>
                    <swiper-slide>
                        <NuxtLink to="/product/1" class="slide purple">
                            <div class="image">
                                <img src="@/assets/img/sale6.png" alt="">
                            </div>

                            <h2>Fiery Soul of the Slayer</h2>

                            <div class="price">
                                <small>
                                    22 800 ₸
                                    <img src="@/assets/img/discount.svg" alt="">
                                </small>
                                <p>19 800 ₸</p>
                            </div>
                        </NuxtLink>
                    </swiper-slide>

                </swiper>

                <div class="navs">
                    <img src="@/assets/img/prev.svg" class="prev" alt="">
                    <img src="@/assets/img/next.svg" class="next" alt="">
                </div>
            </div>
        </div>

        <div class="about">
            <h1>
                о нас
            </h1>
            <img src="@/assets/img/aboutbg.png" class="abg" alt="">
            <div class="about__body">
                <div class="about__left">
                    <div>
                        <p>Dota shop - это не просто интернет-магазин скинов и предметов для Dota 2. Мы — сообщество
                            страстных игроков, которые разделяют вашу страсть к этой увлекательной игре. Наша цель — сделать
                            процесс приобретения скинов и оружия в Dota 2 максимально удобным и приятным для вас.</p>

                        <NuxtLink to="/about">Подробнее</NuxtLink>
                    </div>
                    <img src="@/assets/img/about1.png" alt="">
                </div>
                <div class="about__right">
                    <img src="@/assets/img/about2.png" alt="">
                    <div>
                        <p>Мы предлагаем богатый выбор скинов и оружия для всех персонажей Dota 2, помогая выделиться среди
                            других игроков. Мы страстно следим за индустрией и всегда готовы предоставить самые актуальные и
                            качественные предметы. Для нас важно, чтобы каждая ваша сделка на Dota 2 Skin Market была
                            надежной и
                            приятной.</p>
                    </div>
                </div>
            </div>
        </div>

        <div class="sales popular">
            <h1>популярное</h1>
            <p>Посетите раздел, где быстро найдете самые популярные и стильные предметы, которые выбирают многие игроки</p>

            <div class="sales__slider">
                <swiper :slides-per-view="6" :space-between="30" :navigation="navigation2" :breakpoints="breakpoints"
                    :modules="modules">
                    <swiper-slide>
                        <NuxtLink to="/product/1" class="slide green">
                            <div class="image">
                                <img src="@/assets/img/sale1.png" alt="">
                            </div>

                            <h2>Fiery Soul of the Slayer</h2>

                            <div class="price">
                                <small>
                                    22 800 ₸
                                    <img src="@/assets/img/discount.svg" alt="">
                                </small>
                                <p>19 800 ₸</p>
                            </div>
                        </NuxtLink>
                    </swiper-slide>
                    <swiper-slide>
                        <NuxtLink to="/product/1" class="slide golden">
                            <div class="image">
                                <img src="@/assets/img/sale2.png" alt="">
                            </div>

                            <h2>Fiery Soul of the Slayer</h2>

                            <div class="price">
                                <small>
                                    22 800 ₸
                                    <img src="@/assets/img/discount.svg" alt="">
                                </small>
                                <p>19 800 ₸</p>
                            </div>
                        </NuxtLink>
                    </swiper-slide>
                    <swiper-slide>
                        <NuxtLink to="/product/1" class="slide blackblue">
                            <div class="image">
                                <img src="@/assets/img/sale3.png" alt="">
                            </div>

                            <h2>Fiery Soul of the Slayer</h2>

                            <div class="price">
                                <small>
                                    22 800 ₸
                                    <img src="@/assets/img/discount.svg" alt="">
                                </small>
                                <p>19 800 ₸</p>
                            </div>
                        </NuxtLink>
                    </swiper-slide>
                    <swiper-slide>
                        <NuxtLink to="/product/1" class="slide whiteblue">
                            <div class="image">
                                <img src="@/assets/img/sale4.png" alt="">
                            </div>

                            <h2>Fiery Soul of the Slayer</h2>

                            <div class="price">
                                <small>
                                    22 800 ₸
                                    <img src="@/assets/img/discount.svg" alt="">
                                </small>
                                <p>19 800 ₸</p>
                            </div>
                        </NuxtLink>
                    </swiper-slide>
                    <swiper-slide>
                        <NuxtLink to="/product/1" class="slide calblue">
                            <div class="image">
                                <img src="@/assets/img/sale5.png" alt="">
                            </div>

                            <h2>Fiery Soul of the Slayer</h2>

                            <div class="price">
                                <small>
                                    22 800 ₸
                                    <img src="@/assets/img/discount.svg" alt="">
                                </small>
                                <p>19 800 ₸</p>
                            </div>
                        </NuxtLink>
                    </swiper-slide>
                    <swiper-slide>
                        <NuxtLink to="/product/1" class="slide purple">
                            <div class="image">
                                <img src="@/assets/img/sale6.png" alt="">
                            </div>

                            <h2>Fiery Soul of the Slayer</h2>

                            <div class="price">
                                <small>
                                    22 800 ₸
                                    <img src="@/assets/img/discount.svg" alt="">
                                </small>
                                <p>19 800 ₸</p>
                            </div>
                        </NuxtLink>
                    </swiper-slide>
                    <swiper-slide>
                        <NuxtLink to="/product/1" class="slide purple">
                            <div class="image">
                                <img src="@/assets/img/sale6.png" alt="">
                            </div>

                            <h2>Fiery Soul of the Slayer</h2>

                            <div class="price">
                                <small>
                                    22 800 ₸
                                    <img src="@/assets/img/discount.svg" alt="">
                                </small>
                                <p>19 800 ₸</p>
                            </div>
                        </NuxtLink>
                    </swiper-slide>

                </swiper>

                <div class="navs">
                    <img src="@/assets/img/prev.svg" class="prev2" alt="">
                    <img src="@/assets/img/next.svg" class="next2" alt="">
                </div>
            </div>
        </div>

        <div class="how">
            <h1>как это работает?</h1>
            <img src="@/assets/img/howbg.png" class="howbg" alt="">

            <div class="how__body pc">
                <div>
                    <img src="@/assets/img/how.png" class="img-fluid howitem" alt="">
                    <img src="@/assets/img/neon.svg" alt="" class="neon img-fluid">
                </div>
            </div>
            <div class="how__body mob">
                <img src="@/assets/img/howmob.svg" alt="">
            </div>
        </div>
        <a name="faq"></a>
        <div class="faq">
            <h1>частые вопросы</h1>

            <div class="faq__body">
                <div class="faq__left">
                    <button v-for="faq in faqs" :key="faq.id" :data-target="'#collapseExample' + faq.id"
                        aria-expanded="false" :aria-controls="'collapseExample' + faq.id" @click="toggleCollapse(faq.id)">
                        <div class="inside">
                            <span :style="{ color: faq.isOpen ? '#5D5FEF' : '' }">
                                {{ faq.question }}
                            </span>
                            <img src="@/assets/img/plus.svg" :class="{ rotate: faq.isOpen }"
                                style="transition: all .3s ease;" alt="">
                        </div>

                        <div :class="{ collapse: !faq.isOpen }" style="transition:  all .3s ease;"
                            :id="'collapseExample' + faq.id">
                            <span class="mt-3">Нет, к сожалению Steam не предоставляет никаких способов для вывода средств с
                                их счета.</span>
                        </div>
                    </button>
                </div>
                <div class="faq__right">
                    <img src="@/assets/img/faq.png" class="img-fluid" alt="">
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import { Navigation } from 'swiper/modules';
import { Swiper, SwiperSlide } from 'swiper/vue';
import 'swiper/css';
import 'swiper/css/navigation';
export default {
    components: {
        Swiper,
        SwiperSlide,
    },
    data() {
        return {
            faqs: [
                { id: 1, isOpen: false, question: 'Что делать, если после пополнения баланса деньги не поступили на счет?' },
                { id: 2, isOpen: false, question: 'Что делать, если предмет не пришел или вы не можете его забрать?' },
                { id: 3, isOpen: false, question: 'Что делать, если к вам в стим добавился “наш сотрудник” и предлагает вам двойной баланс за ваши вещи?' },
                { id: 4, isOpen: false, question: 'Можно ли перевести средства со счета Steam?' },
                { id: 5, isOpen: false, question: 'Как продать или вывести предмет с сайта?' },
            ],
            words: [
                { class: 'word word1', letters: [], text: "Инвокера?" },
                { class: 'word word2', letters: [], text: "Валеру?" },
                { class: 'word word3', letters: [], text: "Сережу?" },
                { class: 'word word4', letters: [], text: "Илью?" },
                { class: 'word word5', letters: [], text: "Семена?" }
            ],
            currentWordIndex: 0,
            breakpoints: {
                320: {
                    slidesPerView: 1,
                    spaceBetween: 10,

                },
                1025: {
                    slidesPerView: 3,
                    spaceBetween: 30,
                },
                1300: {
                    slidesPerView: 4,
                    spaceBetween: 30,
                },
                1600: {
                    slidesPerView: 6,
                    spaceBetween: 30,
                }
            },
            modules: [Navigation],
            navigation: {
                nextEl: '.next',
                prevEl: '.prev'
            },
            navigation2: {
                nextEl: '.next2',
                prevEl: '.prev2'
            },
        }
    },
    methods: {

        toggleCollapse(id) {
            const faq = this.faqs.find(f => f.id === id);
            faq.isOpen = !faq.isOpen;
        },

        changeWord() {
            const currentWord = this.words[this.currentWordIndex];
            const nextWordIndex = (this.currentWordIndex === this.words.length - 1) ? 0 : this.currentWordIndex + 1;
            const nextWord = this.words[nextWordIndex];

            for (let i = 0; i < currentWord.letters.length; i++) {
                this.animateLetterOut(currentWord.letters, i);
            }

            for (let i = 0; i < nextWord.letters.length; i++) {
                nextWord.letters[i].class = 'letter behind';
                this.animateLetterIn(nextWord.letters, i);
            }

            this.currentWordIndex = nextWordIndex;
        },
        animateLetterOut(letters, i) {
            setTimeout(() => {
                letters[i].class = 'letter out';
            }, i * 80);
        },
        animateLetterIn(letters, i) {
            setTimeout(() => {
                letters[i].class = 'letter in';
                letters[i].opacity = 1;
            }, 340 + (i * 80));
        }
    },
    mounted() {
        this.words.forEach(word => {
            const content = word.text;

            for (let i = 0; i < content.length; i++) {
                const letter = {
                    char: content[i],
                    class: 'letter',
                    opacity: 0
                };
                word.letters.push(letter);
            }
        });

        setInterval(this.changeWord, 2500);
        this.changeWord();
    }
}
</script>
<script setup>
useSeoMeta({
    title: 'Главная | DotaShop',
    ogTitle: 'Главная | DotaShop',
    description: 'Главная | DotaShop',
    ogDescription: 'Главная | DotaShop',
})
</script>
<style lang="scss" scoped>
.page {
    padding: 130px 52px 87px 150px;

    @media (max-width: 1024px) {
        padding: 150px 20px 70px;
    }

    .faq {

        @media (max-width: 1024px) {
            margin-top: -70px;
        }

        .faq__body {
            display: flex;
            gap: 24px;

            .faq__left {
                width: 100%;
                display: flex;
                flex-direction: column;
                gap: 30px;

                .rotate {
                    transform: rotate(30deg) !important;
                }

                button {
                    width: 100%;
                    max-width: 750px;
                    text-align: left;
                    padding: 9px 15px 9px 10px;
                    border: 1px solid #5D5FEF;
                    background: linear-gradient(90deg, #24212B 0%, rgba(36, 33, 43, 0.65) 100%);
                    z-index: 2;
                    position: relative;
                    transition: all .3s ease;
                    outline: none;
                    box-shadow: none;

                    .inside {
                        display: flex;
                        justify-content: space-between;
                        align-items: center;
                        gap: 20px;
                        height: auto;

                    }

                    span {
                        font-size: 16px;
                        font-style: normal;
                        font-weight: 400;
                        line-height: 130%;
                        font-family: var(--mon);
                        color: #fff;
                        max-width: 686px;
                        display: block;
                        transition: all .3s ease;
                    }

                    .collapse {
                        display: none;
                        transition: height 0.3s ease-in-out;
                    }

                    .collapse.show {
                        display: block;
                    }
                }
            }

            .faq__right {
                width: 100%;

                @media (max-width: 1024px) {
                    display: none;
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
            margin: 0 0 30px;

            @media (max-width: 1024px) {
                font-size: 20px;
                margin: 0 0 20px;
            }
        }
    }

    .how {
        margin-top: 60px;
        position: relative;

        .howbg {
            position: absolute;
            top: -20%;
            left: 10%;

            @media (max-width: 1024px) {
                display: none;
            }
        }

        .mob {
            display: none !important;

            @media (max-width: 1024px) {
                display: flex !important;

                img {
                    width: 100%;
                }
            }
        }

        .pc {
            @media (max-width: 1024px) {
                display: none !important;
            }
        }

        .how__body {
            display: flex;
            justify-content: center;



            div {
                position: relative;

                .howitem {
                    z-index: 2;
                    position: relative;
                }

                .neon {
                    max-width: 100%;
                    position: absolute;
                    left: 20%;
                    top: 8%;
                    z-index: 1;
                    animation: scale 2s infinite;
                    animation-direction: alternate;
                    animation-fill-mode: both;
                }

                @keyframes scale {
                    from {
                        transform: scale(1);
                    }

                    to {
                        transform: scale(1.2);
                    }
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
            margin: 0 0 30px;
        }
    }

    .popular {
        margin-top: 55px;
        z-index: 2;
    }

    .about {
        margin-top: 60px;
        position: relative;

        @media (max-width: 1024px) {
            margin-top: 30px;
        }

        .abg {
            position: absolute;
            top: -20%;
            left: 20%;
            z-index: 1;

            @media (max-width: 1024px) {
                display: none;
            }
        }

        .about__body {
            z-index: 2;
            display: flex;
            align-items: flex-start;
            gap: 20px;
            margin-top: 30px;

            @media (max-width: 1600px) {
                img {
                    max-width: 50%;
                }

                flex-direction: column;
                gap: 15px;
            }

            @media (max-width: 1024px) {
                margin-top: 20px;
            }

            .about__right {
                z-index: 2;
                margin-top: 80px;
                display: flex;
                align-items: flex-end;
                gap: 20px;

                @media (max-width: 1024px) {
                    margin-top: 0;
                }

                p {
                    font-size: 16px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: 130%;
                    font-family: var(--mon);
                    color: #C8C8C8;
                    margin: 0;
                    max-width: 427px;

                    @media (max-width: 1024px) {
                        max-width: 100%;
                    }
                }

                @media (max-width: 1024px) {
                    img {
                        display: none;
                    }
                }
            }

            .about__left {
                z-index: 2;
                display: flex;
                align-items: flex-start;
                gap: 20px;

                @media (max-width: 1024px) {
                    flex-direction: column;
                    gap: 15px;

                    img {
                        max-width: 100%;
                        width: 100%;
                        object-fit: cover;
                    }
                }

                p {
                    font-size: 16px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: 130%;
                    font-family: var(--mon);
                    color: #C8C8C8;
                    margin: 0 0 30px;
                    max-width: 404px;

                    @media (max-width: 1024px) {
                        max-width: 100%;
                    }
                }

                a {
                    font-size: 16px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: 130%;
                    font-family: var(--mon);
                    color: #fff;
                    transition: all .3s ease;

                    padding: 10px 3.281vw;
                    border: 1px solid #5D5FEF;
                    background: #5D5FEF;
                    border-radius: 10px;
                    display: inline-block;
                    text-decoration: none;

                    &:hover {
                        background: #252654;
                    }
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
            margin: 0;

            @media (max-width: 1024px) {
                font-size: 20px;
            }
        }
    }

    .sales {
        z-index: 2;

        @media (max-width: 1024px) {
            margin-top: 30px;
        }

        .sales__slider {
            z-index: 2;

            .navs {
                margin-top: 30px;
                display: flex;
                justify-content: flex-end;
                gap: 20px;
                position: relative;
                z-index: 3;

                img {
                    cursor: pointer;
                }
            }

            .slide {
                padding: 10px;
                display: flex;
                border-radius: 10px;
                flex-direction: column;
                max-width: 250px;
                text-decoration: none;

                @media (max-width: 1024px) {
                    max-width: 100%;
                }

                .image {
                    img {
                        width: 100%;
                        height: 130px;
                        object-fit: cover;
                    }
                }

                h2 {
                    font-size: 16px;
                    font-style: normal;
                    font-weight: 600;
                    line-height: 130%;
                    font-family: var(--mon);
                    color: #fff;
                    margin: 10px 0;
                }

                .price {
                    display: flex;
                    justify-content: flex-end;
                    gap: 6px;

                    small {
                        position: relative;
                        display: block;
                        font-size: 12px;
                        font-style: normal;
                        font-weight: 600;
                        line-height: 130%;
                        font-family: var(--mon);
                        color: #fff;

                        img {
                            position: absolute;
                            bottom: 0;
                            left: 0;
                            top: 0;
                        }
                    }

                    p {
                        font-size: 16px;
                        font-style: normal;
                        font-weight: 600;
                        line-height: 130%;
                        font-family: var(--mon);
                        color: #fff;
                        margin: 0;
                    }
                }
            }

            .green {
                border: 2px solid #ADE55C;
                background: linear-gradient(180deg, #4D4D4D 0%, #121212 100%);
            }

            .golden {
                border: 2px solid #E4AE39;
                background: linear-gradient(90deg, #24212B 0%, rgba(36, 33, 43, 0.65) 100%);
            }

            .blackblue {
                border: 2px solid #3348E0;
                background: linear-gradient(90deg, #24212B 0%, rgba(36, 33, 43, 0.65) 100%);
            }

            .whiteblue {
                border: 2px solid #458AD9;
                background: linear-gradient(90deg, #24212B 0%, rgba(36, 33, 43, 0.65) 100%);
            }

            .calblue {
                border: 2px solid #B0C3D9;
                background: linear-gradient(90deg, #24212B 0%, rgba(36, 33, 43, 0.65) 100%);
            }

            .purple {
                border: 2px solid #7047F2;
                background: linear-gradient(90deg, #24212B 0%, rgba(36, 33, 43, 0.65) 100%);
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
            margin: 0 0 10px;

            @media (max-width: 1024px) {
                font-size: 20px;
            }
        }

        p {
            font-size: 16px;
            font-style: normal;
            font-weight: 400;
            line-height: 130%;
            font-family: var(--mon);
            color: #C8C8C8;
            margin: 0 0 20px;
        }
    }

    .main {
        padding: 0 62px 0 81px;
        height: 100vh;

        @media (max-width: 1024px) {
            padding: 0;
            height: auto;
        }

        .links {
            margin-top: 50px;

            @media (max-width: 1024px) {
                margin-top: 20px;
            }

            p {
                font-size: 20px;
                font-style: normal;
                font-weight: 400;
                line-height: 130%;
                font-family: var(--mon);
                color: #fff;
                margin: 0 0 30px;

                @media (max-width: 1024px) {
                    font-size: 16px;
                }
            }

            .buttons {
                display: flex;
                justify-content: center;
                gap: 30px;

                @media (max-width: 1024px) {
                    gap: 20px;
                }

                a {
                    z-index: 10;
                    padding: 10px 71px;
                    text-decoration: none;

                    font-size: 16px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: 130%;
                    font-family: var(--mon);
                    color: #fff;
                    border: 1px transparent;
                    border-radius: 10px;
                    transition: all .3s ease;

                    @media (max-width: 1024px) {
                        padding: 10px 0;
                        flex: 1;
                    }

                    &:first-child {
                        background: #5D5FEF;
                        border: 1px solid #5D5FEF;

                        &:hover {
                            background: #252654;
                        }
                    }

                    &:last-child {
                        background: #252654;
                        border: 1px solid #5D5FEF;

                        &:hover {
                            background: #5D5FEF;
                        }
                    }
                }
            }
        }

        .cards {
            display: flex;
            justify-content: center;
            margin-top: 70px;
            gap: 30px;

            @media (max-width: 1024px) {
                a {
                    &:nth-child(n + 3) {
                        display: none;
                    }
                }
            }

            @media (max-width: 600px) {
                a {
                    &:nth-child(n + 2) {
                        display: none;
                    }
                }

                margin-top: 10px;
            }
        }

        .bg {
            position: absolute;
            top: 0;
            right: 0;
            pointer-events: none;
        }

        h1 {
            font-size: 64px;
            font-style: normal;
            font-weight: 400;
            line-height: normal;
            letter-spacing: 2.4px;
            font-family: var(--col);
            color: #fff;
            text-align: center;
            display: flex;
            gap: 10px;

            @media (max-width: 1024px) {
                font-size: 24px;
            }

        }

        .rotating-text {
            font-family: 'Open Sans', sans-serif;
            font-weight: 600;
            font-size: 40px;
            // position: absolute;
            width: 450px;
            left: 50%;
            margin-left: -175px;
            height: 40px;
            top: 50%;
            margin-top: -20px;

            @media (max-width: 1024px) {
                margin-left: -50px;
            }

        }

        .rotating-text-pre,
        .rotating-text-suf {
            display: inline-block;
            vertical-align: top;
            margin: 0 0 0 10px;
        }

        .word {
            position: absolute;
        }

        .letter {
            display: inline-block;
            position: relative;
            float: left;
            transform: translateZ(25px);
            transform-origin: 50% 50% 25px;
            -webkit-text-fill-color: transparent;
            background: linear-gradient(180deg, #CF11FF 0%, rgba(74, 147, 255, 0.69) 100%);
            background-clip: text;
            -webkit-background-clip: text;
        }

        .letter.out {
            transform: rotateX(90deg);
            transition: transform 0.32s cubic-bezier(0.55, 0.055, 0.675, 0.19);
        }

        .letter.behind {
            transform: rotateX(-90deg);
        }

        .letter.in {
            transform: rotateX(0deg);
            transition: transform 0.38s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        .word1 {

            color: #fff;
        }

        .word2 {
            color: #2980b9;
        }

        .word3 {
            color: #c0392b;
        }

        .word4 {
            color: #16a085;
        }

        .word5 {
            color: #2c3e50;
        }

        .cardd {
            width: 100%;
            height: 425px;
            position: relative;
            display: flex;
            justify-content: center;
            align-items: flex-end;
            padding: 0 36px;
            perspective: 2500px;
            // margin: 0 50px;
        }

        .cover-image {
            width: 100%;
            max-height: 425px;
            object-fit: cover;
            border-radius: 7.5px;
        }

        .wrapper {
            transition: all 0.5s;
            position: absolute;
            width: 100%;
            z-index: -1;
        }

        .cardd:hover .wrapper {
            transform: perspective(900px) translateY(-5%) rotateX(25deg) translateZ(0);
            box-shadow: 2px 35px 32px -8px rgba(0, 0, 0, 0.75);
            -webkit-box-shadow: 2px 35px 32px -8px rgba(0, 0, 0, 0.75);
            -moz-box-shadow: 2px 35px 32px -8px rgba(0, 0, 0, 0.75);
        }

        .wrapper::before,
        .wrapper::after {
            content: "";
            opacity: 0;
            width: 100%;
            height: 80px;
            transition: all 0.5s;
            position: absolute;
            left: 0;
        }

        .wrapper::before {
            top: 0;
            height: 100%;
            background-image: linear-gradient(to top,
                    transparent 46%,
                    rgba(12, 13, 19, 0.5) 68%,
                    rgba(12, 13, 19) 97%);
        }

        .wrapper::after {
            bottom: 0;
            opacity: 1;
            // background-image: linear-gradient(to bottom,
            //         transparent 46%,
            //         rgba(12, 13, 19, 0.5) 68%,
            //         rgba(12, 13, 19) 97%);
        }

        .cardd:hover .wrapper::before,
        .wrapper::after {
            opacity: 1;
        }

        .cardd:hover .wrapper::after {
            height: 120px;
        }

        .title {
            width: 100%;
            transition: transform 0.5s;
        }

        .cardd:hover .title {
            transform: translate3d(0%, -50px, 100px);
        }

        .character {
            width: 100%;
            opacity: 0;
            transition: all 0.5s;
            position: absolute;
            z-index: -1;
            pointer-events: none;
        }

        .cardd:hover .character {
            opacity: 1;
            transform: translate3d(0%, -30%, 100px);
        }
    }
}
</style>
