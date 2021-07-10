<template>
<div class= "container mt-5">
    <div class="row">
        <div class="col-md-12">
            <div class="card border-0 rounded shadow">
                <div class="card-body">
                    <h4>DATA POST</h4>
                    <hr>
                    <router-link :to="{name : 'post.create'}" class="btn btn-md btn-success">
                        TAMBAH POST</router-link>
                        <table class="table table-striped table-bordered mt-4">
                            <thead class="thead-dark">
                                <tr>
                                <th scoppe="col">TITLE</th>
                                <th scoppe="col">CONTENT</th>
                                <th scoppe="col">OPTIONS</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr v-for="(post, index) in posts" :key="index">
                                    <td>{{ post.title}}</td>
                                    <td>{{ post.content}}</td>
                                    <td class="text-center">
                                        <router-link :to="{name : 'post.edit', params:{id: post,id}}"
                                        class="btn btn-sm btn-primary mr-1">EDIT</router-link>
                                        <button class="btn btn-sm btn-danger mr-1">HAPUS</button>

                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import axios from 'axios'
import { onMounted, ref} from 'vue'

export default {
    setup() {
        let posts = ref([])
        onMounted(() => {
            axios.get('http://novaagustina.online/backendapi/public/api/post')
            .then(response => {
                posts.value = response.data.data
            }).catch(error => {
                console.log(error.response.data)
            })
        })
    return {
        posts
    }
    }
}
</script>

<style>
body{
    background: lightgray;
}
</style>