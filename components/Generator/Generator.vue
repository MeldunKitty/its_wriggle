<template>
    <div class="card card--thin card--centered">
        <div class="card__header">
            <h1>Генератор отчётов</h1>
        </div>
        <div class="card__body">
            <form class="form">
                <div class="form__row">
                    <div class="form__item">
                        <vs-input
                            type="date"
                            v-model="form.date_range_start"
                            label="Начало периода"
                        />
                    </div>
                    <div class="form__item">
                        <vs-input
                            type="date"
                            v-model="form.date_range_end"
                            label="Конец периода"
                            :min="form.date_range_start"
                        />
                    </div>
                    <div class="form__item form__item--w-auto">
                        <vs-switch v-model="form.vacation" success>
                            <template #off>
                                <i class='bx bxs-bot mr-1'></i>У меня не было отпуска
                            </template>
                            <template #on>
                                <i class='bx bxs-volume-mute mr-1'></i>У меня был отпуск
                            </template>
                        </vs-switch>
                    </div>
                </div>
            </form>
        </div>
        <div class="card__footer">
            <div class="generator-result">
                <div class="generator-result__header">
                    <h2>Сгенерированный отчёт</h2>
                    <vs-button :disabled="!result">
                        <i class='bx bx-copy mr-1'></i>Копировать
                    </vs-button>
                </div>

                <div class="generator-result__body">
                    <pre>
                    {{ form }}
                    </pre>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
name: "Generator",

    data() {
        return {
            form: {
                date_range_start: null,
                date_range_end: null,
                vacation: false
            },
            result: null
        }
    },
    watch: {
        form: {
            handler(value) {
                if (value.date_range_end) {

                    const start = new Date(value.date_range_start);
                    const end = new Date(value.date_range_end);

                    if (end <= start) {
                        this.form.date_range_end = null
                    }
                }
            },
            deep: true
        }
    },
}
</script>

<style scoped lang="scss">
.generator-result {
    display: flex;
    flex-direction: column;

    &__header {
        display: flex;
        align-items: center;
        justify-content: space-between;

        font-size: 1.5rem;
        margin-bottom: 0.5rem;
    }

    &__body {
        display: flex;
        flex-direction: column;
        background: rgba(0, 0, 0, .03);
        padding: 1rem;
    }
}
</style>
