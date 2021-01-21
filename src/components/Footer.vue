<template>
  <div>
    <h5 id="drball">DragonBall Twitter</h5>
  </div>
</template>

<script>
export default {
  name: "footer-container"
};
</script>

<style lang="scss" scoped>
#drball {
  font-family: "Press Start 2P", cursive;
  color: black;
  font-size: 10px;
  display: grid;
  align-items: center;
  justify-items: center;
  margin-top: 10vh;
  margin-bottom: 3vh;
}

// TABLET
@media only screen and (min-width: 670px) {
  #drball {
    font-size: 12px;
  }
}
</style>