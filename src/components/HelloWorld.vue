<template>
    <div>
        <input type="text" v-model="searchContent">
        <button @click="searchInfo">点击</button>
    </div>
</template>

<script>
import axios from "axios";
export default {
    name: "HelloWorld",
    data() {
        return {
            searchContent: "",
            receiveInfo:''
        };
    },
    methods: {
        searchInfo() {
            axios.get(`https://api.github.com/search/users?q=${this.searchContent}`).then(response=>{
                this.receiveInfo=response.data.items;
                console.log(this.receiveInfo)
            },error=>{
                console.log(error.message)
            })
        },
    },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
    margin: 40px 0 0;
}
ul {
    list-style-type: none;
    padding: 0;
}
li {
    display: inline-block;
    margin: 0 10px;
}
a {
    color: #42b983;
}
</style>
