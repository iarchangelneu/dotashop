<template>
    <div class="page">
        <h1>Пользовательское соглашение</h1>
    </div>
</template>
<script setup>
useSeoMeta({
    title: 'Пользовательское соглашение | DotaShop',
    ogTitle: 'Пользовательское соглашение | DotaShop',
    description: 'Пользовательское соглашение | DotaShop',
    ogDescription: 'Пользовательское соглашение | DotaShop',
})
</script>
<style lang="scss" scoped>
.page {
    padding: 73px 100px 110px 200px;

    @media (max-width: 1600px) {
        padding: 73px 50px 110px 200px;
    }

    @media (max-width: 1024px) {
        padding: 150px 20px 50px;
    }

    h1 {
        font-size: 32px;
        font-style: normal;
        font-weight: 400;
        line-height: normal;
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

    p {
        font-size: 16px;
        font-style: normal;
        font-weight: 400;
        line-height: 130%;
        font-family: var(--mon);
        color: #fff;
    }
}
</style>