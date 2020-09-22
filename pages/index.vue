<template>
    <div class="page-container">
        <Generator/>
    </div>
</template>

<script>
import Generator from "../components/Generator/Generator";

export default {
    name: 'Index',
    components: {Generator},
    head() {
        return {
            title: 'Генератор отчётов',
            meta: [
                {
                    hid: 'index-description',
                    name: 'description',
                    content: 'Сервис для генерации больших объемов отчётов'
                },
            ]
        }
    },

}
</script>
