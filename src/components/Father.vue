<template>
    <div>
        <div :style="{fontSize: postFontSize+'em'}">
            <Son v-for="post in posts" :key="post.id" :post="post" @enlarge-text="postFontSize+=$event" />
        </div>
        <button @click="log">aa</button>
    </div>
    
</template>

<script>
import Son from "./Son.vue"

export default {
    components:{
        Son,
    },

    data:()=>({
        posts: [{id:1,title:"a",content:"hello"},{id:2,title:"b",content:"goodbye"}],
        postFontSize: 1,
    }),
    methods:{
    }
}
</script>