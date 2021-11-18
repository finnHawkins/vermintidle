<template>
    <div class="modal">
        <div class="modeSelectorContainer">
            <div class="modeSelector">
                <div class="modeList">
                    <div class="mode" v-for="mode in modes" :key="mode.mName">
                        <div class="modeImg">
                        </div>
                        <div class="modeData">
                            <p> {{ mode.mName }}</p>
                            <p> {{ mode.mDesc }} </p>
                        </div>
                    </div>
                </div>
            </div>
            <div class="modeBtnContainer">
                <button>Select</button>
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

        }

    }
    
}
</script>