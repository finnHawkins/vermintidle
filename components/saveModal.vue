<template>
    <div class="modal">
        <div class="saveSelectorContainer">
            <div class="saveSelector">
                <saveDisplay newSave=true />
                <saveDisplay v-bind:newSave="false" characterID="0" v-bind:gameMode="1" lastLogin="18/11/2021" />
                <saveDisplay newSave=true />
            </div>
        </div>
    </div>

</template>

<script>
export default {
    


}
</script>