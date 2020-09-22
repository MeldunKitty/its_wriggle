<template>
    <div class="page-container">
        тут страница эбаут
    </div>
</template>

<script>
import Card from "../components/Card/Card";
export default {
    name: 'About',
    components: {Card},
    head() {
        return {
            title: 'О проекте',
            meta: [
                {
                    hid: 'about-description',
                    name: 'description',
                    content: 'Немного о сервисе генераций отчётов'
                },
            ]
        }
    }
}
</script>
