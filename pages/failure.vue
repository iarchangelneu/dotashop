<template>
    <div class="page">
        <h1>Ошибка при выполнении транзакции</h1>
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
    title: 'Ошибка при выполнении транзакции | DotaShop',
    ogTitle: 'Ошибка при выполнении транзакции | DotaShop',
    description: 'Ошибка при выполнении транзакции | DotaShop',
    ogDescription: 'Ошибка при выполнении транзакции | DotaShop',
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