<template>
    <div class="modal">
      <div class="characterSelectorContainer">
        <div class="characterSelector">
          <div class="characterList">
            <characterDisplay v-for="character in characters" :key="character" v-bind="character" v-on:click.native="toggleCareers(character)" />
          </div>
          <div class="characterCareers" v-if="selectedCharacterID != 0">
            <div v-for="career in characters[selectedCharacterID -1].careers" :key="career.careerID" class="characterCareer" v-on:click="getCareerID(career)" v-bind:style="selectedCareerID == career.careerID  ? 'background-color: #192943' : ''">
              <div class="careerDetails">
                <img :src="getImgSrc(career.careerLogoSrc)">
                <p v-bind:style="characters[selectedCharacterID -1].cLevel >= career.careerLevelReq ? 'color: white' : 'color: black' ">{{ career.careerName}}</p>
              </div>
            </div>
          </div>
          <div class="buttonContainer">
            <div class="buttonBannerContainer">
              <button :disabled="disableButton()" v-on:click="emitCharacter()">Confirm</button>
              <div class="infoBanner" v-if="disableButton() && selectedCareerID > 0">You need to level up this character more before you can play this class!</div>
            </div>
          </div>
        </div>
      </div>
    </div>
</template>

<script>

import characterData from "~/assets/json/characters.json";

export default {

  data() {

    return {

      characters: characterData,
      selectedCharacterID: 0,
      selectedCareerID: 0,

    }

  },

  methods: {

    toggleCareers(character) {

      // if the character isn't already selected
      // sets all the other characters' selected vlaues to false
      if(!character.selected) {

        for (let i = 0; i < 5; i++) {
          this.characters[i].selected = false;
        }
        this.selectedCharacterID = character.cID;

      } else {
        this.selectedCharacterID = 0;
      }
      this.selectedCareerID = 0;
      character.selected = !character.selected;

    },

    getImgSrc(fileName) {

      return require('~/assets/imgs/characters/' + fileName + '.png');
    
    },

    getCareerID(career) {

      this.selectedCareerID = career.careerID;

    },

    disableButton() {

      let disabled = true;

      //if both a character and a career have been selected
      //ensure the career is available to the player
      if((this.selectedCareerID === 0 || this.selectedCharacterID === null) || (this.selectedCareerID === 0 && this.selectedCharacterID === null)) {
        disabled = true;
      } else {
        
        let character = this.characters.find(c => c.cID === this.selectedCharacterID);

        if(character.careers[this.selectedCareerID -1].careerLevelReq <= character.cLevel) {
          disabled = false;
        } else {
          disabled = true;
        }
      }

      return disabled;

    },

    emitCharacter() {

      this.$emit('confirmCharacter', {
        characterID: this.selectedCharacterID,
        careerID: this.selectedCareerID
      });

    }

  }

}
</script>