<script>
// import axios from 'axios';
import {store} from '../store';

export default {
    data() {
        return {
            store,
        };
    },
    props: {
        project: {
            type: Object,
            required: true,
        
        }
        // title: {
        //     type: String,
        //     required: true
        // },
        // description: {
        //     type: String,
        //     required: true
        // },
        // image: {
        //     type: String,
        //     required: true
        // },
        // id: {
        //     type: Number,
        //     required: true
        // }
    },
    methods: {
        getImageUrl(image) {
			return image
				? this.store.baseUrl + 'storage/' + image
				: this.store.baseUrl + 'storage/default.jpg';
		},
    }
};
</script>

<template>
    <div class="card" style="width: 18rem;">
        <!-- <img :src="this.store.baseUrl + 'storage/' + project.image" class="card-img-top" :alt="project.id"> -->
        <img :src="getImageUrl(project.image)" class="card-img-top" :alt="project.id">
        <div class="card-body">
            <h5 class="card-title">{{ project.title }}</h5>
            <p class="card-text">{{ project.description }}</p>
            <div v-for="technology in project.technologies" :key="technology.name">{{ technology.name }}</div>
            <div>{{ project.type.name }}</div>
            <router-link :to="{ name: 'projects.show', params: { slug: project.slug } }" class="btn btn-primary">view</router-link>
        </div>
    </div>
</template>

<style lang="scss" scoped>
img {
    height: 150px;
    object-fit: contain;
}
</style>