<template>
    <div>
        <ul>
            <ii v-for="m in messages" :key="m.text">
                {{m.text}}
            </ii>
        </ul>
    </div>
</template>

<script>
import {mapState} from 'vuex';
export default {
    middleware:['chat'],
    head(){
        return{
            title:`Room number ${this.user.room}`
        }
    },
    computed:mapState(['user','messages'])
}

</script>