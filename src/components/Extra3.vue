<template>
    <div>
        <div v-for="(value,name,index) in object" :key="name">
            {{index}}.{{name}}: {{value}} 
        </div>
        <input type="number" max="100" v-model="num"/>
        <button @click="oddEven">Odd/Even</button>
        <ul v-if="odd">
            <li v-for="(n,i) in oddNumbers" :key="i">{{n}}</li>  
        </ul>
        <ul v-else>
            <li v-for="(n,i) in evenNumbers" :key="i">{{n}}</li>  
        </ul>
        <ul>
            <li v-for="(n,i) in multiple" :key="i">{{n}}</li>  
        </ul>
        <ul v-for="(set,i) in sets" :key="i">
            <li v-for="(n,i) in even(set)" :key="i">{{n}}</li>  
        </ul>
    </div>
</template>

<script>
export default {
    data:()=>({
        object:{
            title: "How to do lists in Vue",
            author: "John Doe",
            published_on: "2016-04-10",
        },
        numbers: [1,2,3,4,5,6,7,8,9,10,11,12,13],
        odd:true,
        num:1,
        sets: [[1,2,3,4,5],[6,7,8,9,10]]
    }),
    computed:{
        evenNumbers: function(){
            return this.numbers.filter(function(number){
                return number%2===0
            })
        },
        oddNumbers: function(){
            return this.numbers.filter(function(number){
                return number%2===1
            })
        },
        multiple: function(){
            return this.numbers.filter(this.filterMultiple)
        },
    },
    methods:{
        oddEven: function(){
            this.odd = !this.odd
        },
        filterMultiple: function(number){
            return number%this.num===0
        },
        even: function(numbers){
            return numbers.filter(function(number){
                return number%2===0
            })
        }
    }
}
</script>