<template>
    <div class="text-center mt-4">
        <h4>Your Score is {{ result }} ms</h4>
        <div v-if="result > 45 && result <= 450">
            <p class="text-success fw-bold">Congratulations! You are so fast &#127942;</p>
        </div>
        <div v-else-if="result >= 500 && result < 900">
            <p class="text-secondary fw-bold">Congratulations! You are normal &#127881;</p>
        </div>
        <div v-else="">
            <p class="text-danger fw-bold">You are too late Plz Try Again! &#128170;</p>
        </div>
    </div>
</template>

<script>
    export default {
        props : ['result']
    }
</script>

<style scoped>

</style>