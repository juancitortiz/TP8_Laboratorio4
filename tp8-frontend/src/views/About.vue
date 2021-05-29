<template>
  <div class="about">
    <GmapMap
  :center="{lat:-32.886306, lng:-68.838297}"
  :zoom="15"
  map-type-id="terrain"
  style="width: 100%; height: 100vh"
    >
  <GmapMarker
    :position="{lat:-32.886306, lng:-68.838297}"
    :clickable="true"
    :draggable="true"
    @click="center={lat:-32.886306, lng:-68.838297}"
    />
  </GmapMap>
  </div>
</template>
