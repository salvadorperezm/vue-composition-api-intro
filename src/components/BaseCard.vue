<template>
    <section class="section">
        <slot></slot>
    </section>
</template>

<script setup></script>

<style scoped>
.section {
    border-radius: 10px;
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
    padding: 16px;
    margin: 40px auto;
    max-width: 600px;
}
</style>