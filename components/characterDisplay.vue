<template>
    <div class="character">
        <div class="characterInfo">
            <div class="characterLevel">{{ cLevel }}</div>
            <div class="characterDetails">
                <div class="characterPortrait"><img :src="getImgSrc(cIcon)"></div>
                <div class="characterText">
                    <div class="characterName">{{ cName }}</div>
                </div>
            </div>
        </div>
        <div class="characterCareers">
            <div v-for="career in careers" :key="career.careerName" class="characterCareer">
                <div class="careerDetails">
                    <img :src="getImgSrc(career.careerLogoSrc)">
                    <p v-bind:style="cLevel >= career.careerLevelReq ? 'color: white' : 'color: black' ">{{ career.careerName}}</p>
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