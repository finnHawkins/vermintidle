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
      displayCharacterSelector: true,
      displaySettings: false,
      displaySaves: false,
      displayInventory: false,

    }

  },

}
</script>
