<template>
    <ul class="header__menu">
        <li class="header__link" 
            v-for="link in links"
            :key="link">
            <a href="#">{{link}}</a>    
        </li>
    </ul>
</template>

<script>
export default {
    props: ["links"]
}
</script>
<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Merriweather:wght@300&display=swap');
$font: 'Merriweather', serif;
    .header__menu{
        padding: 0;
        list-style: none;
        display: flex;
        justify-content: space-around;
        width: 100%;
    }
    .header__link{
        a{
            font-family: $font;
            font-size: 14px;
            line-height: 150%;
            color: #343030;
            text-decoration: none;
        }
    }
</style>