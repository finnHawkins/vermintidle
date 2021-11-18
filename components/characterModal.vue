<template>
    <div class="modal">
      <div class="characterSelector">
        <characterDisplay v-for="character in characters" :key="character" v-bind="character" v-on:click.native="toggleCareers(character)" />
      </div>
    </div>
</template>

<script>

import characterData from "~/assets/json/characters.json";

export default {

  data() {

    return {

      characters: characterData,

    }

  },

  methods: {

    toggleCareers(character) {

      if(!character.selected) {

        for (let i = 0; i < 5; i++) {
          this.characters[i].selected = false;
        }

      }
      character.selected = !character.selected;

    }

  }

}
</script>