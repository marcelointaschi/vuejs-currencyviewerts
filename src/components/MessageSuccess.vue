<template>
<div class="message-container">
    <p>{{ msg }}</p>
</div>
    
</template>
<script lang="ts">
import { defineComponent, PropType} from 'vue'

export default defineComponent({
    name: "MessageSuccess",
    props:{
        msg: {
            required : true,
            type: String
        }
    }
});
</script>
<style scoped>
.message-container{
    color: #004085;
    background-color: #CCE5FF;
    border: 2px solid #B8DAFF;
    border-radius: 5px;
    padding: 10px;
    max-width: 400px;
    margin: 0 left;
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
}
</style>
