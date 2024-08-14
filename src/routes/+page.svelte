<script lang="ts">
  let isEnabled = false;

  function isEnabledOrDisabled() {
    isEnabled = !isEnabled;
    console.log("isEnabled: " + isEnabled);
  }
</script>

<body>
  <div class="div-container">
    <span>regular</span>
    <div class="div-row-container">
      <div class="regular-square">
        <span>I'm just a regular square</span>
      </div>
    </div>
  </div>
  <div class="div-container">
    <span>pseudo-class</span>
    <div class="div-row-container">
      <div class="pseudo-class-square-hover">
        <h4>Pseudo class: hover</h4>
        <span>Hover me</span>
      </div>
      <div class="pseudo-class-square-active">
        <h4>Pseudo class: active</h4>
        <span>Click me</span>
      </div>
      <div class="pseudo-class-square-transition">
        <h4>Pseudo class: hover</h4>
        <span>Hover me to scale</span>
      </div>
      <div class="pseudo-square-class-not-container" class:enabled={isEnabled}>
        <div class="pseudo-square-class-not" on:click={isEnabledOrDisabled}>
          <span class="pseudo-square-class-not-text">Click me to expand</span>
        </div>
      </div>
    </div>
  </div>
  <div class="div-container">
    <span>animated</span>
    <div class="div-row-container">
      <div class="square-animated">
        <h4>Animate with @keyframes</h4>
      </div>
    </div>
  </div>
</body>

<style lang="scss">
  body {
    padding: 0;
    margin: 0;
    background-color: rgb(196, 243, 255);
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow-x: hidden;
    flex-direction: column;
    gap: 10px;
  }

  .div-container {
    align-items: center;
    justify-content: center;
    display: flex;
    flex-direction: column;
  }

  .div-row-container {
    padding: 24px;
    flex-direction: row;
    display: flex;
    gap: 10px;
  }

  .regular-square {
    height: 250px;
    width: 250px;
    background-color: rgb(120, 120, 190);
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .pseudo-class-square-hover {
    height: 250px;
    width: 250px;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    background-color: rgb(120, 120, 190);

    &:hover {
      background-color: red;
    }
  }

  .pseudo-class-square-active {
    height: 250px;
    width: 250px;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    background-color: rgb(120, 120, 190);

    &:active {
      background-color: red;
    }
  }

  .pseudo-class-square-transition {
    height: 250px;
    width: 250px;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    background-color: rgb(120, 120, 190);
    transition: transform 1s; /* Apply transition to the base state to animate
    exiting of hover as well */

    &:hover {
      background-color: red;
      transform: scale(1.2, 1.2); /* Scale up on hover */
    }
  }

  @keyframes square-animation {
    from {
      background-color: rgb(120, 120, 190);
    }
    to {
      background-color: red;
    }
  }

  @keyframes square-animation-percentage {
    0% {
      background-color: rgb(120, 120, 190);
    }
    25% {
      background-color: red;
    }
    50% {
      background-color: blue;
    }
    100% {
      background-color: green;
    }
  }

  .square-animated {
    height: 250px;
    width: 250px;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: rgb(120, 120, 190);
    animation-name: square-animation;
    animation-duration: 5s;
    animation-direction: alternate;
    animation-timing-function: ease-in-out;
    animation-iteration-count: infinite;
  }

  .pseudo-square-class-not-container {
    width: 250px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .pseudo-square-class-not-container:not(:enabled) .pseudo-square-class-not {
    height: 100px;
    width: 100px;
    background-color: green;
    text-align: center;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: transform 1s;
    transform: scale(1, 1);
  }

  .pseudo-square-class-not-container.enabled .pseudo-square-class-not {
    background-color: red;
    color: white;
    text-align: center;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: transform 1s;
    transform: scale(2.5, 2.5);
  }

  .pseudo-square-class-not-container:not(:enabled)
    .pseudo-square-class-not-text {
    color: black;
    transition: color 1s;
  }

  .pseudo-square-class-not-container.enabled .pseudo-square-class-not-text {
    color: white;
    transition: color 1s;
  }
</style>
