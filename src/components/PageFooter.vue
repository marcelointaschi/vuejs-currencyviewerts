<template>
    <div id="footer">
        <p> Currency converter &copy; 2022</p>
    </div>
</template>
<script lang="ts">
import { defineComponent} from 'vue'

export default defineComponent({
    name: "PageFooter"
});
</script>
<style scoped>
#footer {
    height: 40px;
    background-color: rgb(30, 52, 100);
    border-top: 10px solid rgb(30, 52, 100);
    color: #FFF;
    position: fixed;
    justify-content: center;
    align-items: center;
    text-align: center;
    width: 100%;
    bottom: 0px;
    left: 0px;
    right: 0px;
    margin-bottom: 0px;
}

</style>
