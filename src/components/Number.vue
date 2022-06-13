<template>
    <input placeholder="Please enter" v-model="input1" /><br>
    <button @click="isNumber">Is this a number?</button><br>
    <input placeholder="Please enter" v-model="input2" /><br>
    <button @click="append">Append</button><br>
    <button @click="show">Show the array</button><br>
    <ol v-if="seen">
      <li v-for="(todo,i) in myArray" :key="i">{{todo}}</li>
      <!-- v-for iterates all the elements and creates them in HTML, 
      v-for requires an index and we need a key to hold this-->
    </ol><br>
    <input placeholder="Please enter the array" v-model="input3" /><br>
    <input placeholder="Added value:" v-model="input4" /><br>
    <button @click="arrayAdd">Add</button><br>
    <ol v-if="seen2">
      <li v-for="(todo,i) in myArray2" :key="i">{{todo}}</li>
      <!-- v-for iterates all the elements and creates them in HTML, 
      v-for requires an index and we need a key to hold this-->
    </ol><br>

    
</template>

<script>
export default {
    data: () => ({
        input1: undefined,
        input2: undefined,
        myArray: [],
        seen: false,
        seen2: false,
        input3: undefined,
        input4: undefined,
        myArray2: [],
    }),
    methods:{
        arrayAdd: function(){
            this.myArray2 = this.input3.split(",")
            this.myArray2 = this.myArray2.map(element => {
                return Number(element) + Number(this.input4)
            });
            this.seen2 = true
        },
        isNumber: function(){
           if(isNaN(this.input1)){
               window.alert("This is not a number")
           }
           else{
               window.alert("This is a number")
            //  .toString(a) can change something to the ath base (range: 2-36)  
           }
        },
        append: function(){
            if (this.input2==null){
                this.myArray.push("null")
            }
            else{
                this.myArray.push(this.input2)
            }
            this.input2 = null
            this.seen = true
        },
        show: function(){
            this.seen = !this.seen
        },
        
    },
}
</script>