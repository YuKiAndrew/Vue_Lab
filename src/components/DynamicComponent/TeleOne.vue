

<template>
  <div>
    <h2>Component</h2>
    <p>This is the inside of the component.</p>
    <Teleport to="#TeleportTwo">
      <div id="redDiv">Hello!</div>
    </Teleport>
  </div>
</template>

<script>

</script>

<style>
#redDiv {
  background-color: lightcoral;
  margin: 10px;
  padding: 10px;
  display: inline-block;
}
</style>