<template>
    <section class="container">
        <h2 class="section-h2">Блоги</h2>
        <div class="blogs-carousel">
            <carousel :dots="false" :auto-width="true" :nav="false" :margin="24">
                <template slot="prev">
                    <button class="btn-circle btn-outline-primary prev-month" type="button">
                        <span class="gr-harmonics">retertert</span>
                    </button>
                </template>
                <template slot="next">
                    <button class="btn-circle btn-outline-primary next-month" type="button">
                        <span class="gr-harmonics">qeqeqweq</span>
                    </button>
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
        </div>
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
