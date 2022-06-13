<template>
    <div>
        <button v-for="(tab,index) in tabs" :key="index" @click="pagename=tab">{{tab}}</button>
        <Tabs2 :pagename="pagename" />
    </div>
</template>

<script>

import Tabs2 from "./Tabs2.vue"

export default {
    components:{
        Tabs2,

    },
    data:()=>({
        tabs: ["Home","Posts",'Archives'],
        pagename: "Home"
    })
}
</script>
