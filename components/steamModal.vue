<template>
    <div class="modal fade" id="steamModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
        <div class="modal-dialog modal-dialog-centered">
            <div class="modal-content">

                <div class="modal-body">
                    <h1>вывести предмет в steam</h1>

                    <div class="text-center">
                        <p>Вы хотите вывести <strong>Fiery Soul of the Slayer</strong> в Steam?</p>
                        <p>Инструкция по получению предмета будет отправлена на Вашу почту</p>

                        <button>ПОДТВЕРДИТЬ</button>
                    </div>
                </div>

            </div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {}
    }
}
</script>

<style lang="scss" scoped>
.modal-body {
    padding: 0;

    h1 {
        font-size: 24px;
        font-style: normal;
        font-weight: 400;
        line-height: 130%;
        /* 31.2px */
        letter-spacing: 1.2px;
        text-transform: uppercase;
        font-family: var(--col);
        color: #fff;
        margin: 0 0 30px;

        @media (max-width: 1024px) {
            text-align: center;
            font-size: 16px;
            margin: 0 0 20px;
        }
    }

    button {
        border-radius: 10px;
        border: 1px solid var(--iris-100, #5D5FEF);
        background: var(--iris-100, #5D5FEF);
        padding: 10px 20px;

        font-size: 16px;
        font-style: normal;
        font-weight: 400;
        line-height: 130%;
        font-family: var(--mon);
        color: #fff;
    }

    p {
        font-size: 16px;
        font-style: normal;
        font-weight: 400;
        line-height: 130%;
        font-family: var(--mon);
        color: #fff;
        margin: 0 0 18px;
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