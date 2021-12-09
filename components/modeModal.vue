<template>
    <div class="modal">
        <div class="modeSelectorContainer">
            <div class="modeSelector">
                <div class="modeList">
                    <div class="mode" v-for="mode in modes" :key="mode.mName" @click="getModeID(mode)" v-bind:style="selectedModeID == mode.mID  ? 'background-color: #192943' : ''">
                        <div class="modeImg">
                        </div>
                        <div class="modeData">
                            <p class="modeName"> {{ mode.mName }}</p>
                            <p class="modeDesc"> {{ mode.mDesc }} </p>
                        </div>
                    </div>
                </div>
                <div class="modeBtnContainer">
                    <button :disabled="disableButton()" @click="emitMode()">Select</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

import modeData from '~/assets/json/modes.json';

export default {

    data() {

        return {

            modes: modeData,
            selectedModeID: 0

        }

    },

    methods: {

        getModeID(mode) {

            this.selectedModeID = mode.mID;

        },

        disableButton() {

            let disabled = true;

            //if both a character and a career have been selected
            //ensure the career is available to the player
            if(this.selectedModeID === 0) {
                disabled = true;
            } else {
                
                disabled = false;
            }

            return disabled;

        },

        emitMode() {

            this.$emit('confirmMode', {
                modeID: this.selectedModeID
            });

        }
    }
    
}
</script>