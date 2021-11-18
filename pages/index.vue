<template>
  <div class="mainScreen">
    <saveModal v-if="displaySaves" />
    <characterModal v-if="displayCharacterSelector" />
    <settingsModal v-if="displaySettings" />
    <modeModal v-if="displayModeSelector" />

  </div>
</template>

<script>

export default {

  data() {

    return {
      displayCharacterSelector: false,
      displayModeSelector: false,
      displaySettings: false,
      displaySaves: false,
      displayInventory: false,

    }

  },

}
</script>
