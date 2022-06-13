<template>
    <div>
        <input :placeholder="[[pagename]] +' component' ">
    </div>
</template>

<script>
export default {
    props:{
        pagename:undefined,
    },
    data:()=>({
        // place:this.pagename+" component"
    })
}
</script>