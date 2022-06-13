<template>
    <div>
        <h3>{{post.title}}</h3>
        <button @click="$emit('enlarge-text',0.1)">Enlarge Text</button>
        <div v-html="post.content"></div>
    </div>
</template>

<script>
export default {
    props:{
        post: undefined
    }
}
</script>