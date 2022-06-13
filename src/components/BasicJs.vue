<template>
    <div>
        <p id="demo" v-if="seen">Javascript can change HTML content.</p>
        <button type="button" onclick='document.getElementById("demo").innerHTML="Hello Javascript!"'>Click Me!</button>
        <button @click="myFunction">Function</button><br><br>
        Enter a sentence:<br>
        <input v-model="sentence" /><br>
        Start:<br>
        <input placeholder="Please enter a number" v-model="start" /><br>
        End:<br>
        <input placeholder="Please enter a number" v-model="end" /><br>
        <button @click="chop">Get slice</button><br>
        What do you want to locate?:<br>
        <input v-model="locate" /><br>
        <button @click="location">Get location</button><br>
        What do you want to replace this with?<br>
        <input v-model="replace" /><br>
        <button @click="replaceReplace">Replace</button><br>
        <button @click="changeCase">Change case</button><br>
    </div>
</template>

<script>
export default {
    data:()=>({
        person: {
            firstName: "john",
            lastName: "Doe",
            id : 5566,
            fullName: function(){
                return this.firstName + " " + this.lastName
            }
        },
        sentence: null,
        locate: null,
        seen: false,
        start: null,
        end: null,
        replace: undefined,
        case: true,
    }),
    methods:{
        myFunction: function(){
            var carName = 'Volvo';
            function print(){
                console.log(carName)
            }
            print()
        },
        location: function(){
            if(this.sentence.indexOf(this.locate)==-1){
                window.alert("Not found")
                return
            }
            window.alert(this.sentence.indexOf(this.locate)) 
            // indexOf(str,position to start searching)
            // lastIndexOf

        },
        chop: function(){
            // if(this.end<=this.start){
            //     window.alert("The starting index has to be smaller than the ending index")
            //     return
            // }
            // if(this.start>this.sentence.length){
            //     window.alert("The starting index has to be within the range of the given setence")
            //     return
            // }
            // substring and slice are the same but substring only accepts positive
            // substr(a,b) a:position, b:the length of the substring eg. setence.substr(3,7)
            if((this.start==null)&&(this.end==null)){
                window.alert("Please check your input")
                return
            }
            if(Number(this.start)>this.sentence.length-1){
                window.alert("Please check your input")
                this.start = null
                this.end = null
                return
            }
            if((Number(this.start)<this.sentence.length)&&this.end==undefined){
                window.alert(this.sentence.slice(Number(this.start)))
                return
            }
            
            else if((this.start==0)&&(Number(this.end)<0)){
      
                window.alert(this.sentence.slice(Number(this.start),Number(this.end)))
                return
            }
            else if((Number(this.end)>Number(this.start))&&this.end!=0){
     
                window.alert(this.sentence.slice(Number(this.start),Number(this.end)))
                return
            }
            window.alert("Please check your input")
            this.start = null
            this.end = null
        },
        replaceReplace: function(){
            var re = new RegExp(this.locate,"ig")
            this.sentence = this.sentence.replace(re,this.replace)
            window.alert("Replace Completed")
        },
        changeCase: function(){
            if(this.case){
                this.sentence = this.sentence.toUpperCase()
                this.case = !this.case
            }
            else{
                this.sentence = this.sentence.toLowerCase()
                this.case = !this.case
            }
            // "H".charCodeAt(0) gives you the ASCII of 'H'
            // .split("") same as python
            
        },
    }
    
}
</script>

<style scoped>
    input{
        width: 200px;
    }
</style>