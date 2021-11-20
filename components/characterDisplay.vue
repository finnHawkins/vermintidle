<template>
    <div class="character">
        <div class="characterInfo" v-bind:style="selected  ? 'background-color: #192943' : '' ">
            <div class="characterDetails">
                <div class="characterPortrait"><img :src="getImgSrc(cIcon)"></div>
                <div class="characterText">
                    <div class="characterLevel">{{ cLevel }}</div>
                    <div class="characterName">{{ cName }}</div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    
    props: {
        cName: String,
        cID: Number,
        cIcon: String,
        cLevel: Number,
        imgLink: String,
        careers: Array,
        selected: Boolean
    },

    methods: {

        getImgSrc(fileName) {

            return require('~/assets/imgs/characters/' + fileName + '.png');
              

        }

    }

}
</script>