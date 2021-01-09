<template>
    <app-layout>
        <template #header>
            {{ course.titre }}
        </template>
        <div class="py-4 mx-8">
            <div class="text-2xl">{{ this.courseShow.episodes[this.currentKey].titre }}</div>
            <iframe class="w-full h-screen" :src="this.courseShow.episodes[this.currentKey].video_url" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
            <div class="text-sm text-white-300">{{ this.courseShow.episodes[this.currentKey].description }}</div>
            <div class="mt-6">
                <ul v-for="(episode, index) in this.courseShow.episodes" :key="episode.id">
                    <li class="mt-3 flex justify-between items-center">
                        <div>
                            Episode n°{{ index + 1 }} - {{ episode.titre }}
                            <button class="text-gray-500 focus:text-indigo-500" @click="switchEpisode(index)">
                                Voir l'épisode
                            </button>
                        </div>
                        <progress-button :episode-id="episode.id" />
                    </li>
                </ul>
            </div>
        </div>
    </app-layout>
</template>

<script>
    import AppLayout from './../../Layouts/AppLayout'
    import ProgressButton from './ProgressButton'

    export default {
        components: {
            AppLayout,
            ProgressButton
        },
        data(){
            return{
                courseShow: this.course,
                currentKey: 0
            }
        },
        props: ['course'],
        methods:{
            switchEpisode(index){
                this.currentKey = index;

                window.scrollTo({
                    top: 0,
                    left: 0,
                    behavior: 'smooth'
                })
            }
        },
        mounted() {},
    }
</script>