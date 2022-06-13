<template>
    <div>
        <button @click="show=!show">
            Toggle
        </button>
        <transition name="fade">
            <p v-if="show">Hello</p>
        </transition>

        <button @click="show = !show">
            Toggle render
        </button>
        <transition name="slide-fade">
            <p v-if="show">hello</p>
        </transition>
    </div>
</template>

<script>
export default {
    data:()=>({
        show:true,
    }),
}
</script>

<style>
    .fade-enter-active{
        transition: opacity .5s ease-in;
        opacity: 1;
    }
    .fade-leave-active{
        transition: opacity .5s;
    }
    .fade-enter{
        opacity: 0 !important;
    }
    .fade-leave-to{
        opacity: 0;
    }
    .slide-fade-enter-active {
        transition: all .8s ease;
    }
    .slide-fade-leave-active {
        transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
    }
    .slide-fade-enter, .slide-fade-leave-active{
        transform: translateX(10px);
        opacity: 0;
    }
</style>