<template>
  <div class="mainScreen">
    <saveModal v-if="currentDisplay === 1" />
    <characterModal v-if="currentDisplay === 2" @confirmCharacter="onCharacterConfirmation" />
    <modeModal v-if="currentDisplay === 3" @confirmMode="onModeConfirmation" />
    <settingsModal v-if="displaySettings" />
    <statsModal v-if="displayStats" />

  </div>
</template>

<script>

export default {

  data() {

    return {

      //toggle different modals
      displaySettings: false,
      displayInventory: false,
      displayStats: false,
      
      //relate to current values such as save, character and career, and mode
      currentSaveID: 0,
      currentCharacterID: 0,
      currentModeID: 0,
      
      //controls some of the modals that follow a linear progression
      //1 = save selector
      //2 = character selector
      //3 = mode selector
      //4 = game screen
      currentDisplay: 0

    }

  },

  mounted() {

    this.currentDisplay = 2;
    this.displaySaves = false;
    this.displayInventory = false;

  },

  methods: {

    onCharacterConfirmation({characterID, careerID}) {

      console.log(characterID + ", " + careerID);
      this.currentDisplay = 3;

    },

    onModeConfirmation({modeID}) {

      console.log(modeID);
      this.currentDisplay = 4;

    }



  }

}
</script>
