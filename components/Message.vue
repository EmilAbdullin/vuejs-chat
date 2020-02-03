<template>
    <div>
        <div v-if="name ==='admin'" class="system-message">
            <p class="text-xs-center">{{text}}</p>
            <hr>
        </div>
        <div v-else class="wrap">
            <div class="mes" :class="{owner}">
                <small>
                    <strong>{{name}}</strong>
                    <p>{{text}}</p>
                </small>
            </div>
        </div>
    </div>
</template>


<script>
export default {
    props:{
        name:String,
        text:String,
        owner:{
            type:Boolean,
            default:false
        }
    }
}
</script>


<style scoped>

.system-message{
    margin-bottom:1rem;
}

.system-message > p{
    margin-bottom:1rem;
}

.wrap{
    display:flex;
    flex-direction:column
}

.mes{
    padding:1rem;
    width:60%;
    margin:0 1rem;
    box-shadow:0 1px 0 0 rgba(50,50,50,.3);
    border-radius:4px;
    background:#1976d2;
    position: relative;
    margin-bottom: 1rem;
}

.mes > p{
        margin-bottm:0;
}
.owner{
   background:#fff;
   color:#000;
   align-self:flex-end;
}

</style>