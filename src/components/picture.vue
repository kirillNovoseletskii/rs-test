<template>
    <div :class="price?'body__picture':'body__picture sailed_picture'">
        <img :src="src" class="picture_img">
        <div class="picture-info">
            <div class="picture__titles">
                <h2 class="title">«{{title}}»</h2>
                <h2 class="title">{{author}}</h2>
            </div>
            <div :class="price?'picture__sale-form':'sailed-picture__price'">
                <div class="picture__price-box">
                    <h4 v-if="discount" class="discount">{{price+1000000}} $</h4>
                    <h3 v-if="price" class="picture-price">{{price}} $</h3>
                </div>
                <button 
                    @click="addToCart"
                    :class="inCart?'picture__buy-btn incart':'picture__buy-btn no-cart'" 
                    :style="loading?'cursor:progress; background: #C1B4B1;':'cursor:pointer;'"
                    :disabled='inCart'
                    v-if="price">
                    <svg v-if="inCart" width="16" height="13" viewBox="0 0 16 13" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M14.5315 1.80937L5.63341 11.237L1.34814 7.19237" stroke="#F4F6F9" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg>
                    {{inCart?'В корзине':'Купить'}}
                </button>
                <h3 v-else class="sailed">Продана на аукционе</h3>
            </div>
        </div>
    </div>
</template>
<script>
import axios from 'axios'
export default {
    props: ["src", "title", "author", "price", "discount", 'inCart'],
    data() {
        return {
            loading: false,
            inCartLoc: false
        }
    },
    methods: {
        addToCart(){
            this.loading = true
            axios
                .get('https://jsonplaceholder.typicode.com/posts/1')
                .then(() => {
                    this.loading = false
                    this.$emit('addToCart', this.title)
            });
        }
    }
}
</script>
<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Merriweather:wght@300&display=swap');
$font: 'Merriweather', serif;
    .sailed_picture{
        position: relative;
        &::before{
            z-index: 100;
            content: '';
            position: absolute;
            width: 100%;
            height: 100%;
            background: rgba(255, 255, 255, 0.575);
        }
    }
    .body__picture{
        border: 1px solid #E1E1E1;
        height: 328px;
        .picture_img{
            width: 100%;
            height: 45%;
        }
        .picture-info{
            height: 100%;
            box-sizing: border-box;
            padding:20px 24px 24px 24px;
            .picture__titles{
                margin-bottom: 22px;
                .title{
                    font-style: normal;
                    font-weight: bold;
                    font-size: 18px;
                    line-height: 150%;
                    margin: 0;
                    font-family: $font;
                }
            }
            .sailed-picture__price{
                position: relative;
                height: 48px;
                width: 100%;
                display: flex;
                align-items: center;
                justify-content: flex-start;
                .sailed{
                    font-size: 16px;
                    color: #343030;
                    font-family: $font;
                }
            }
            .picture__sale-form{
                height: 48px;
                width: 100%;
                display: flex;
                align-items: center;
                justify-content: space-around;
                .picture__buy-btn{
                    height: 100%;
                    width: 118px;
                    border: none;
                    color: white;
                    transition: .3s;
                    &:focus{
                        outline: none;
                    }
                }
                .no-cart{
                    background: #382E2B;
                    &:hover{
                        background: #776763;
                    }
                }
                .incart{
                    background: #5B3A32;
                }
                .picture__price-box{
                    display: flex;
                    flex-direction: column;
                    justify-content: center;
                    height: 100%;
                    .discount{
                        margin: 0;
                        font-size: 14px;
                        font-family: $font;
                        text-decoration-line: line-through;
                        color: #A0A0A0;
                    }
                    .picture-price{
                        margin: 0;
                        color: #343030;
                        font-size: 16px;
                        font-family: $font;
                    }
                }
                
            }
        }
    }
</style>