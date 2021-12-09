<template>
  <div class="mainScreen">
    <saveModal v-if="currentDisplay === 1" />
    <characterModal v-if="currentDisplay === 2" @confirmCharacter="onCharacterConfirmation" />
    <modeModal v-if="currentDisplay === 3" @confirmMode="onModeConfirmation" />
    <settingsModal v-if="displaySettings" />
    <statsModal v-if="displayStats" />

    <main>
      <nav>
        <button id="btnSave">Save</button>
        <button disabled>Character Select</button>
        <button disabled>Mode Select</button>
        <button>Inventory</button>
        <button @click="displaySettings = true">Settings</button>
        <button @click="displayStats = true">Stats</button>
      </nav>
      <div class="gameScreen">
        <div class="progressContainer">
          <div class="progressStats">
            <div class="progressBarContainer">
              <div class="progressBar">
                <div id="progressCompleted"></div>
              </div>
            </div>
            <div class="statsContainer">
              <div id="enemyKC">Enemies killed:</div>
              <div id="specialKC">Specials killed:</div>
              <div id="eliteKC">Elites killed:</div>
            </div>
          </div>
          <div class="toggleOptionsContainer">
            <div id="toggleAtk">Auto attack? <input type="checkbox"></div>
            <div id="togglePickup">Auto pickup loot? <input type="checkbox"></div>
            <div id="toggleConsume">Auto use potions/bombs? <input type="checkbox"></div>
          </div>
        </div>
        <div class="enemiesContainer">

          <div class="enemyContainer">
            <div class="enemyName">
            </div>
            <div class="enemyImgContainer">
            </div>
            <div class="enemyHealthbar">
              <span id="enemyHealthText"></span>
              <span id="enemyAvailableHealth"></span>
              <span id="enemyLostHealth"></span>
            </div>
          </div>

        </div>
        <div class="playerContainer">
          <div class="controlButtonsContainer">
            <span><button>Attack</button></span>
            <span><button>Spec Attack</button></span>
            <span><button>Block</button></span>
          </div>
          <div class="playerStatsContainer">
            <div class="playerInfo">
              <div class="playerImage">
              </div>
              <div class="playerLoadoutContainer">
                <div class="loadout">
                  <div id="weapon1"></div>
                  <div id="weapon2"></div>
                  <div id="healthPot"></div>
                  <div id="potion"></div>
                  <div id="bomb"></div>
                </div>
                <div class="blockContainer">
                  <div class="blockIcon"></div>
                  <div class="blockIcon"></div>
                  <div class="blockIcon"></div>
                  <div class="blockIcon"></div>
                  <div class="blockIcon"></div>
                </div>
              </div>
              <div class="playerBuffsContainer">
                <div></div>
                <div></div>
                <div></div>
                <div></div>
                <div></div>
                <div></div>
                <div></div>
              </div>
            </div>
            <div class="playerBars">
              <div class="playerHealthBar">
                <span id="healthText"></span>
                <span id="availableHealth"></span>
                <span id="lostHealth"></span>
                <span id="grimoireHealth"></span>
              </div>
              <div class="specBar">
                <span id="specFull"></span>
                <span id="specEmpty"></span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </main>

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
      currentCareerID: 0,
      currentModeID: 0,

      //controls some of the modals that follow a linear progression
      //1 = save selector
      //2 = character selector
      //3 = mode selector
      //4 = game screen
      currentDisplay: 0,
    }
  },

  mounted() {
    this.currentDisplay = 2
    this.displaySaves = false
    this.displayInventory = false
  },

  methods: {
    onCharacterConfirmation({ characterID, careerID }) {
      console.log(characterID + ', ' + careerID)
      this.currentCharacterID = characterID
      this.currentCareerID = careerID
      this.currentDisplay = 3
    },

    onModeConfirmation({ modeID }) {
      console.log(modeID)
      this.currentModeID = modeID
      this.currentDisplay = 4
    },
  },
}
</script>

