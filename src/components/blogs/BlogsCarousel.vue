<template>
    <section class="container">
        <h2 class="section-h2">Блоги</h2>
        <carousel :dots="false" :auto-width="true" :nav="false" :margin="24" class="blogs-carousel">
            <template slot="prev">
                <div class="carousel-controls carousel-controls_prev">
                    <button class="button carousel-controls__button" type="button">
                        <i class="las la-angle-left"></i>
                    </button>
                </div>
            </template>
            <template slot="next">
                <div class="carousel-controls carousel-controls_next">
                    <button class="button carousel-controls__button" type="button">
                        <i class="las la-angle-right"></i>
                    </button>
                </div>
            </template>
            <div v-for="(blog, bInd) in blogs" :key="bInd" class="box box_white box_blog-item" :title="blog.title">
                <div class="box__header">
                    <img :src="blog.image" alt="Изображение для блога" />
                    <div class="box__header-over">
                        {{ blog.type }}
                    </div>
                </div>
                <div class="box__body">
                    <h3 class="box__body-title">
                        {{ blog.title }}
                    </h3>
                    <div class="box__body-date">
                        {{ blog.date }}
                    </div>
                </div>
            </div>
        </carousel>
    </section>
</template>

<script>
import Carousel from 'vue-owl-carousel';

export default {
    data: () => {
        return {
            blogs: [
                {
                    type: 'Новости',
                    title: 'Marspo Awards 2020: российских букмекеров наградили за лучшие маркетинговые',
                    date: '10 июля 19:09',
                    image: '/img/blog.png'
                },
                {
                    type: 'Новости',
                    title: 'Marspo Awards 2020: российских букмекеров наградили за лучшие маркетинговые',
                    date: '10 июля 19:09',
                    image: '/img/blog.png'
                },
                {
                    type: 'Новости',
                    title: 'Marspo Awards 2020: российских букмекеров наградили за лучшие маркетинговые',
                    date: '10 июля 19:09',
                    image: '/img/blog.png'
                },
                {
                    type: 'Новости',
                    title: 'Marspo Awards 2020: российских букмекеров наградили за лучшие маркетинговые',
                    date: '10 июля 19:09',
                    image: '/img/blog.png'
                },
                {
                    type: 'Новости',
                    title: 'Marspo Awards 2020: российских букмекеров наградили за лучшие маркетинговые',
                    date: '10 июля 19:09',
                    image: '/img/blog.png'
                },
                {
                    type: 'Новости',
                    title: 'Marspo Awards 2020: российских букмекеров наградили за лучшие маркетинговые',
                    date: '10 июля 19:09',
                    image: '/img/blog.png'
                },
            ]
        }
    },
    components: {
        Carousel
    },
}
</script>
