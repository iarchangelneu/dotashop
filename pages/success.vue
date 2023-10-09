<template>
    <div class="page">
        <h1>Транзакция прошла успешно!</h1>
    </div>
</template>
<script>
export default {
    data() {
        return {}
    }
}
</script>
<script setup>
useSeoMeta({
    title: 'Успешная транзакция | DotaShop',
    ogTitle: 'Успешная транзакция | DotaShop',
    description: 'Успешная транзакция | DotaShop',
    ogDescription: 'Успешная транзакция | DotaShop',
})
</script>
<style lang="scss" scoped>
.page {
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
}

h1 {
    font-size: 42px;
    font-family: var(--col);
    color: #fff;
    text-align: center;

    @media (max-width: 1024px) {
        font-size: 25px;
    }
}
</style>