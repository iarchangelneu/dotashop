<template>
    <div class="modal fade" id="modalSecond" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
        <div class="modal-dialog modal-dialog-centered">
            <div class="modal-content">

                <div class="modal-body">
                    <div class="text-center">
                        <img src="@/assets/img/modal2.png" alt="">

                        <h1><strong>{{ name }}</strong> успешно выставлен на продажу!</h1>
                        <p>Если предмет будет продан - Ваш баланс на сайте обновится </p>
                    </div>
                </div>

            </div>
        </div>
    </div>
</template>
<script>
export default {
    props: {
        name: String,
    },
    data() {
        return {}
    }
}
</script>

<style lang="scss" scoped>
.modal-body {
    padding: 0;

    h1 {
        font-size: 16px;
        font-style: normal;
        font-weight: 400;
        line-height: 130%;
        font-family: var(--mon);
        color: #fff;
        margin: 20px 0 18px;
    }

    p {
        font-size: 16px;
        font-style: normal;
        font-weight: 400;
        line-height: 130%;
        font-family: var(--mon);
        color: #fff;
        margin: 0;
    }
}

.modal-content {
    border-radius: 10px;
    background: var(--Bg2, #160E21);
    box-shadow: 0px 4px 16px 0px rgba(86, 31, 140, 0.30);
    padding: 30px;
    border: 0;
}

.modal-dialog {
    max-width: 596px;
    margin: 1.75rem auto;
}
</style>