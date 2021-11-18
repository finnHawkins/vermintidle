<template>
  <div class="mainScreen">
    <saveModal v-if="displaySaves" />
    <characterModal v-if="displayCharacterSelector" />
  </div>
</template>

<script>

export default {

  data() {

    return {
      displayCharacterSelector: false,
      displaySettings: false,
      displaySaves: true,
      displayInventory: false,

    }

  },

}
</script>
