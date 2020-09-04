<template>
    <header class="header">
        <div class="header__items">
            <div class="header__logo">
            <rsLogo/>
        </div>
        <nav class="header__nav">
            <rsLinks :links='links'/>
        </nav>
        <div class="header__search">
            <input 
                type="text" 
                class="header__input"
                placeholder="Поиск по названию картины"
            >
            <button class="header__search-btn">
                Найти
            </button>
        </div>
        </div>
    </header>
</template>
<script>
import rsLogo from './rs-logo'
import rsLinks from './rs-links'
export default {
    components: {
        rsLogo,
        rsLinks
    },
    data() {
        return {
            links: ["Каталог", "Доставка", "Оплата", "Контакты", "О галерее"]
        }
    }
}
</script>
<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Merriweather:wght@300&display=swap');
$font: 'Merriweather', serif;
    .header{
        box-sizing: border-box;
        padding: 0 5%;
        max-width: 100%;
        height: 96px;
        display: flex;
        align-items: center;
        justify-content: center;
        border-bottom:1px solid #E1E1E1;
        &__items{
            width: 100%;
            display:grid;
            grid-template-columns: 0.3fr 0.8fr 0.9fr;
            grid-template-rows: 1fr;
        }
        &__logo{
            display: flex;
            justify-content: flex-end;
        }
        &__search{
            display: flex;
            justify-content: center;
            align-items: center;
        }
        &__nav{
            display: flex;
            justify-content: flex-start;
        }
        &__input{
            width: 294px;
            font-family: $font;
            height: 44px;
            border: 1px solid #E1E1E1;
            padding-left: 16px;
            transition: 0.1s;
            &:focus{
                outline: none;
                border: 1px solid #B5B5B5;
            }
            &::placeholder{
                color: #9F9F9F;
                font-family: $font;
            }
        }
        &__search-btn{
            width: 122px;
            font-family: $font;
            height: 48px;
            background: #403432;
            border: none;
            color: white;
            transition: 0.2s;
            &:hover{
                background: #776763;
            }
            &:focus{
                outline: none;
            }
        }
    }
</style>