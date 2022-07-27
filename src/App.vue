<template>
    <div class="box">
        <div class="heading">
            <h1>Four Forms of Tiga UltraMan</h1>
            <p>Please hover over the image to view all four forms</p>
        </div>
        <div class="img">
            <!-- I used v-on for makeing changes to the src attribute when the mouse hovers -->
            <!-- I used v-bind for reassigning the image src -->
            <img @mouseover="changeImage" alt="Tiga UltraMan" :src="srcUrl" />
        </div>
    </div>
</template>

<script>
export default {
    name: "App",
    data() {
        // I defined the following variables
        // srcIndex is for finding the index of the picture to be dispalyed in the pictures array
        // pictures is an array of Strings which stores the name of the image to be displayed
        // srcUrl is a String which stores the actual value of the image src
        // images is what I copied from the source code in your Robot demonstation project
        return {
            srcIndex: 0,
            pictures: [],
            srcUrl: String,
            images: require.context("./assets", true, /\.png$/),
        };
    },
    created() {
        // When the page is created, I put in four picture names into the pictures array
        this.pictures = ["./1.png", "./2.png", "./3.png", "./4.png"];
    },
    mounted() {
        // When the page is mounted, I assigned the initial image src to be the first value in the pictures array
        this.srcUrl = this.images(this.pictures[this.srcIndex]);
    },
    methods: {
        // This function increments the current index by one, and if it exceeds the length of the pictures array, it will go back to index 0
        // Then the srcUrl is updated to be the new image name which the new index
        changeImage: function () {
            this.srcIndex = (this.srcIndex + 1) % this.pictures.length;
            this.srcUrl = this.images(this.pictures[this.srcIndex]);
        },
    },
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 4rem;
    text-align: center;
}

.box {
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
}

img {
    object-fit: cover;
    max-width: 1080px;
    max-height: 720px;
    width: 80vw;
    height:auto;
}
</style>
