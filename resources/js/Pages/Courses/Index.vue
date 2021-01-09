<template>
    <app-layout>
        <template #header>
            Liste des formations
        </template>
        <div class="py-4" v-for="course in this.courseList" :key="course.id">
            <div class="mx-8 bg-gray-200 rounded shadow p-4">
                <div class="text-sm text-white-300">Mise en ligne par {{ course.user.name }} - <span class="textgray-500 text-sm">{{ course.participants }} participant<span v-if="parseInt(course.participants) > 1 ">s</span></span></div>
                <div class="flex justify-between items-center">
                    <div class="text-4xl">{{ course.titre }}</div>
                    <div>{{ course.episodes_count }} épisodes</div>
                </div>
                <div class="text-sm text-white-300">{{ course.description }}</div>
                <a :href="'course/' + course.id" class="bg-indigo-500 text-white px-2 py-1 text-sm mt-3 inline-block rounded hover:bg-indigo-700">Voir la formation</a>
            </div>
        </div>
    </app-layout>
</template>

<script>
    import AppLayout from './../../Layouts/AppLayout'
    export default {
        components: {
            AppLayout
        },
        props: ['courses'],
        data(){
            return{
                courseList: this.courses
            }
        },
        mounted() {
            
        }
    }
</script>

<style lang="css" scoped>

</style>