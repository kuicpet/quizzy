<template>
    <div>
        <b-nav tabs>
            <b-nav-item disabled class="logo">Quizzy</b-nav-item>
            <b-nav-item disabled class="counter">Counter: 4/10</b-nav-item>
        </b-nav>
    </div>
</template>

<script>
export default {
    name : 'Header'
}
</script>

<style scoped>
    .logo {
        font-weight: bold;
    }
    .counter {
        margin-right: auto;
    }
</style>