<template>
<div class="message-container">
    <p>{{ msgerr }}</p>
</div>
    
</template>
<script lang="ts">
import { defineComponent} from 'vue'

export default defineComponent({
    name: "MessageError",
    props:{
        msgerr: {
            required : true,
            type: String
        }
    }
});
</script>
<style scoped>
.message-container{
    color: #ff0000;
    background-color: #e6b2b2;
    border: 2px solid #e09e9e;
    border-radius: 5px;
    padding: 10px;
    max-width: 400px;
    margin: 0 left;
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
}
</style>
