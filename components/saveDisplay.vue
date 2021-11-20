<template>
    <div class="saveContainer">
        <div class="saveDetails">
            <div class="newSave" v-if="newSave">
                <p>New Save</p>
            </div>
            <div class="saveFile" v-else>
                <div class="characterInfo">
                    <div class="characterImg">
                        <img :src="characterImg" />
                    </div>
                    <div class="characterData">
                        <p class="characterName"> {{ this.characters[this.characterID].cName }} </p>
                        <p class="characterCareer"> {{ this.characters[this.characterID].careers[this.careerID].careerName }} </p>
                        <p class="characterCareer"> {{ this.characters[this.characterID].cLevel }} </p>
                    </div>
                </div>
                <div class="modeInfo">
                    <div class="modeImg">
                    </div>
                    <p> {{ modeText }}</p>
                </div>
                <div class="lastLoginInfo">
                    <p> {{ lastLogin }}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

import characterData from "~/assets/json/characters.json";

export default {
    
    props: {
        newSave: {
            type:Boolean,
            required: true
        },
        characterID: {
            type: Number,
            default: 1
        },
        careerID: {
            type: Number,
            default: 0
        },
        gameMode: {
            type: Number,
            default: 0
        },
        lastLogin: {
            type:Date,
            default: ""
        },

    },

    data() {

        return {

            characters: characterData,

        }

    },

    computed: {

        modeText() {

            let gameModeText = "";

            switch (this.gameMode) {
                case 1:
                    gameModeText = "Slapping rats in horde mode";
                    break;
                case 2:
                    gameModeText = "Saving the world in campaign mode";
                    break;
                case 3:
                    gameModeText = "Madlad traversing the madlands";
                    break;
                
            }

            return gameModeText;


        },

        characterImg() {

            const fileName = this.characters[this.characterID].careers[this.careerID].careerLogoSrc;
            return require('~/assets/imgs/characters/' + fileName + '.png');

        }

    }


}
</script>