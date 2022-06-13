<template>
    <div>
        <input type="text" v-model="message">
        <!-- this shows that computed is still listening and reacts when you change the text -->
        <!-- <p>Original Message: "{{message}}"</p> -->
        <p>Computed Reversed Message: "{{reversedMessage}}"</p>
        <div>{{fullName1}} <br> {{lastName1}} <br> {{firstName1}}</div>
        <input type="text" v-model="fullName1">
        
    </div>
</template>

<script>

export default {
    data:()=>({
        message:'Hello',
        firstName: 'Foo',
        lastName: 'Bar',
        firstName1: '',
        lastName1: '',
    }),
    computed:{
        reversedMessage: function(){
            return this.message.split('').reverse().join('')
        },
        fullName1:{
            get: function(){
                return this.firstName + ' ' + this.lastName
            },
            set: function(newValue){
                var names = newValue.split(' ')
                console.log(names)
                this.firstName1 = names[0]
                this.lastName1 = names[names.length-1]
            }
        }
    },
    // If you use methods:{} instead, add () to reversedMessage
    // watch:{
    //     firstName: function(val){
    //         console.log("YES")
    //         this.fullName = val + ' ' + this.lastName
    //     },
    //     lastName: function(val){
    //         this.fullName = this.firstName + ' ' + val
    //     }
    // }
    
}
</script>