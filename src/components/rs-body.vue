<template>
    <main class="body">
        <h1 class="body__title">Картины эпохи Возрождения</h1>
        <rsCatalog/>
    </main>
</template>
<script>
import rsCatalog from './rs-catalog'
export default {
    components: {
        rsCatalog
    }
}
</script>
<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Merriweather:wght@300;700&display=swap');
    .body{
        width: 100%;
        max-height: 100%;
        height: 100%;
        overflow-x: hidden;
        box-sizing: border-box;
        padding: 0 5%;
        margin-top: 45px;
        display: flex;
        flex-direction: column;
        &__title{
            font-style: normal;
            font-weight: bold;
            font-size: 24px;
            line-height: 150%;
            font-family: 'Merriweather', serif;
            margin-bottom: 39px;
        }

    }
</style>