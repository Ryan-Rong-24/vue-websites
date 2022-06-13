<template>
    <div>
        <button @click = "parse">Click</button><br>
        <p id="demo"></p>
    </div>
</template>

<script>
export default {
    data: () => ({
        text: '{ "employees" : [' +
            '{ "firstName":"John" , "lastName":"Doe" },' +
            '{ "firstName":"Anna" , "lastName":"Smith" },' +
            '{ "firstName":"Peter" , "lastName":"Jones" } ]}',
    }),
    methods:{
        parse: function(){
            var obj = JSON.parse(this.text)
            window.alert(obj)
            document.getElementById("demo").innerHTML = obj.employees[1].firstName + " " + obj.employees[1].lastName
        }
        
    }
}
</script>