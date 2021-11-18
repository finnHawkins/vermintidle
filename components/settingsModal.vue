<template>
    <div class="modal">
        <div class="settingsDisplayContainer">
            <div class="settingsContainer">
                <div class="settingsList">
                    <div class="setting">
                        <p>Auto pickup grimoires and tomes during campaigns?</p>
                        <input type="checkbox" id="switch" /><label for="switch">Toggle</label>
                    </div>
                    <div class="setting">
                        <p>Auto progress to the next campaign?</p>
                        <input type="checkbox" id="switch" /><label for="switch">Toggle</label>
                    </div>
                    <div class="setting">
                        <p>Auto use items picked up during runs, e.g. healing items?</p>
                        <input type="checkbox" id="switch" /><label for="switch">Toggle</label>
                    </div>
                </div>
            </div>
            <div class="settingsBtnContainer">
                <button>Cancel</button>
                <button>Save</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    
}
</script>