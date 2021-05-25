<template>
    <div class="body__catalog">
        <rsPicture
            @addToCart='addToCart'
            v-for="pict in pict_data"
            :key="pict.id"
            :src='pict.src'
            :title="pict.title"
            :author='pict.author'
            :price='pict.price'
            :discount='pict.discount'
            :inCart='pict.inCart'
        />
    </div>
</template>

<script>
import rsPicture from './picture'
export default {
    components: {
        rsPicture
    },
    data: () => ({
        pict_data: [
            {
                id: 1,
                src: require('../assets/1.png'), 
                title: 'Рождение Венеры', 
                author: 'Сандро Боттичелли',
                price: 1000000,
                discount: true,
                inCart: false
                },
                {
                id: 2,
                src: require('../assets/2.jpg'),
                title: 'Тайная вечеря',
                author: 'Леонардо да Винчи ',
                price: 3000000,
                discount: false,
                inCart: false
            },
            {
                id: 3,
                src: require('../assets/3.png'),
                title: 'Сотворение Адама',
                author: 'Микеланджело',
                price: 5000000,
                discount: true,
                inCart: true
            },
            {
                id: 4,
                src: require('../assets/4.png'),
                title: 'Урок анатомии',
                author: 'Рембрандт'
            }
        ]
    }),
    methods: {
        addToCart(val){
            this.pict_data.filter(i => i.title == val)[0].inCart = true
            const parsed = JSON.stringify(this.pict_data)
            localStorage.setItem('data', parsed);
        }
    },
    mounted(){
        if (localStorage.getItem('data')) {
            try {
                this.pict_data = JSON.parse(localStorage.getItem('data'));
            } catch(e) {
                localStorage.removeItem('data');
            }
        }
    }
}
</script>

<style lang="scss">
    .body__catalog{
        width: 100%;
        height: 90%;
        display: grid;
        grid-template-columns: 280px 280px 280px 280px;
        grid-template-rows: 328px;
        grid-column-gap: 32px;
        
    }
</style>