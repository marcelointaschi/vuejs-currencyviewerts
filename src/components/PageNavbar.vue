<template>
    <div id="nav">
        <img :src="logo" :alt="alt" id="logo">
        <RouterLink to="/"><b>Home</b></RouterLink>
        <RouterLink to="/about"><b>About</b></RouterLink>
    </div>
</template>
<script lang="ts">
import { defineComponent} from 'vue'

export default defineComponent({
    name:"PageNavbar",
    props: ["logo","alt"]
})
</script>
<style scoped>
#nav {
    background-color: rgb(30, 52, 100);
    border-bottom: 4px solid rgb(30, 52, 100);
    
    padding: 15px 50px;
    display: flex;
    justify-content: flex-end;
    align-items: center;
}
#nav a {
    color: #FFF;
    text-decoration: none;
    margin: 12px;
    transition: .5s;
}
#nav a:houver{
    color: #FFF;
}
#logo {
    margin: auto;
    margin-left: 0;
    width: 60px;
}
</style>
