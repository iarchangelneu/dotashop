<template>
    <div class="back">
        <button @click="goBack">
            <img src="@/assets/img/back.svg" alt="" loading="lazy">
            <span>Назад</span>
        </button>
    </div>
</template>
<script>
export default {
    methods: {
        goBack() {
            this.prevPage = this.$nuxt.$router.go(-1);
        },
    },
}
</script>
<style lang="scss" scoped>
.back {
    button {
        border-radius: 10px;
        border: 1px solid var(--iris-100, #5D5FEF);
        background: var(--iris-100, #5D5FEF);
        padding: 10px 20px;
        display: flex;
        align-items: center;
        gap: 10px;

        font-size: 16px;
        font-style: normal;
        font-weight: 400;
        line-height: 130%;
        font-family: var(--mon);
        color: #fff;
    }
}
</style>