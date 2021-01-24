<template>
    <div>
        <b-nav tabs>
            <b-nav-item disabled class="logo">Quizzy</b-nav-item>
            <b-nav-item disabled class="counter">Counter: {{ numCorrect }}/{{ numTotal }} </b-nav-item>
        </b-nav>
    </div>
</template>

<script>
export default {
    name : 'Header',
    props: [
        "numCorrect",
        "numTotal"
    ]
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