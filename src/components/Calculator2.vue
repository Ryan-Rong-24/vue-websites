<template>
    <div>
        <input type="text" v-model="equation"><br>
        <button @click="equation=''">C</button><br>
        <button @click="equation+='7'">7</button>
        <button @click="equation+='8'">8</button>
        <button @click="equation+='9'">9</button>
        <button @click="equation+='+'">+</button><br>
        <button @click="equation+='4'">4</button>
        <button @click="equation+='5'">5</button>
        <button @click="equation+='6'">6</button>
        <button @click="equation+='-'">-</button><br>
        <button @click="equation+='1'">1</button>
        <button @click="equation+='2'">2</button>
        <button @click="equation+='3'">3</button>
        <button @click="equation+='*'">*</button><br>
        <button @click="equation+='0'">0</button>
        <button @click="equation+='.'">.</button>
        <button @click="equation+='÷'">÷</button>
        <button @click="equation+='^'">^</button>
        <button @click="equation+='!'">!</button>
        <button @click="equation+='P'">nPr</button>
        <button @click="equation+='C'">nCr</button>
        <button @click="execute">=</button>
    </div>
</template>

<script>
export default {
    data:()=>({
        equation: "",
    }),
    methods:{
        execute:function(){
            /*eslint-disable*/
            var a = new RegExp(/[\+\-\*\/÷\^!PC]/)
            var b = new RegExp(/\d*\.?\d+/)
            var ans = 0
            var nums = this.equation.split(a).map(Number)
            var c = this.equation.split(b)
            if(c[c.length-1]==""){
                var ops = c.slice(1,-1)
            } else {
                var ops = c.slice(1)
            }
            // var ops = this.equation.split(b).slice(1,-1)
            console.log(c)
            console.log(nums,ops)
            if(ops[0]=="+"){
                this.equation=nums[0]+nums[1]
            }
            else if(ops[0]=="-"){
                this.equation=nums[0]-nums[1]
            }
            else if(ops[0]=="*"){
                this.equation=nums[0]*nums[1]
            }
            else if(ops[0]=="/"||ops[0]=="÷"){
                this.equation=nums[0]/nums[1]
            }
            else if(ops[0]=="^"){
                this.equation=nums[0]**nums[1]
            }
            else if(ops[0]=="!"){
                var sum = nums[0]
                for(var i=nums[0]-1;i>=1;i--){
                    sum*=i
                }
                this.equation=sum
            }
            else if(ops[0]=="C"){
                this.equation=this.fact(nums[0])/(this.fact(nums[1])*this.fact(nums[0]-nums[1]))
            }
            else if(ops[0]=="P"){
                this.equation=this.fact(nums[0])/this.fact(nums[0]-nums[1])
            }
        },
        fact: function(num){
            var sum = num
            for(var i=num-1;i>=1;i--){
                sum*=i
            }
            return sum
        }
    }
}
</script>

<style scoped>

</style>