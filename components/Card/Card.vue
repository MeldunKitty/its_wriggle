<template>
    <div class="card">
        <slot>

        </slot>
    </div>
</template>

<style scoped lang="scss">
.card {
    display: flex;
    flex-direction: column;
    box-shadow: 0 5px 20px 0 rgba(0, 0, 0, var(--vs-shadow-opacity));
}
</style>
