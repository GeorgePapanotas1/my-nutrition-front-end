<template>
  <div class="entrance-component">
    <div class="greet-section">
      <h2>Welcome to Nutrio</h2>
    </div>
    <div class="information-text">
      <p>
        In this version of Nutrio, you can register a nutrition routine. The
        scope of the project is to allow users to keep track of their nutrition
        routine and use statistics to perform better.
      </p>
    </div>
    <div class="spacer"></div>
    <div class="button-start">
      <button @click="$router.push('register')" class="green-button">
        Begin
      </button>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped lang="scss">
.greet-section {
  h2 {
    font-size: 40px !important;
    font-weight: 400;
  }
}

.information-text {
  p {
    line-height: 1.7;
    width: 80%;
    margin: auto;
  }
}

.button-start {
  .green-button {
    background-color: #aaca5b;
    padding: 16px 64px;
    border-radius: 7px;
    border: 1px solid #9c9797;
    color: white;
    font-weight: 800;
  }

  .green-button:focus {
    outline: none !important;
  }

  .green-button:hover {
    background-color: #839c43;
    cursor: pointer;
  }
}
</style>
