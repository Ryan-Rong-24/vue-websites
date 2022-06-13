<template>
    <div>
<!-- HTML validation: -->
        <input type="number" step="3"> 

        <input type="submit">
    </div>
</template>

<script>
export default {
    data:()=>({
        d: new Date(),
        // how to create a date: new Date() #get date now, 
        //                       new Date(year,month,day,hours,minutes,seconds,milliseconds) #have to have at least two
        //                       new Date(milliseconds)
        //                       new Date(date string)
        // date strings:         ("YYYY-MM-DD")
        //                       ("YYYY-MM")
        // ISO                   ("YYYY-MM-DDTHH:MM:SSZ")
        // Z:GMT, to change timezone, replace Z with +HH:+MM/-HH:-MM
        // short                 ("MM/DD/YYYY")
    }),
}
</script>