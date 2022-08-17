<template>
<div v-if="event">
<h1>{{event.title}}</h1>
<p>{{event.time}} @ {{event.date}}</p>
<p>{{event.description}}</p>
</div>
</template>
<script>
import EventService from '@/services/EventService'
export default{
    props:['id'],
    data(){
        return {
            event:null,
        }
    },
    created(){
        //fetch api
        EventService.getEvent(this.id).then(res =>{
            this.event=res.data
        }).catch(error=>{
            console.log(error)
        })
    }
}
</script>