<script setup>
import IconPlus from "./icons/IconPlus.vue";
import IconMinus from "./icons/IconMinus.vue";

function numChange(btn) {
  const myInput = document.getElementById("my-input");
  let id = btn.target.getAttribute("id");
  let min = myInput.getAttribute("min");
  let max = myInput.getAttribute("max");
  let step = myInput.getAttribute("step");
  let val = myInput.value;
  let calcStep =
    id === "searchBar__numChangeBox__increaseBtn" ? step * 1 : step * -1;
  let newValue = parseInt(val) + calcStep;

  if (newValue >= min && newValue <= max) {
    myInput.value = newValue;
  }
}
</script>

<template>
  <div class="searchBar__numChangeBox">
    <button id="searchBar__numChangeBox__decreaseBtn" @click="numChange">
      <div class="searchBar__numChangeBox__decreaseBtn__icon">
        <IconMinus class="searchBar__numChangeBox__decreaseBtn__icon__svg" />
      </div>
    </button>
    <input
      type="number"
      min="1"
      max="100"
      step="1"
      value="1"
      id="my-input"
      readonly
      class="searchBar__numChangeBox__inputField"
    />
    <button id="searchBar__numChangeBox__increaseBtn" @click="numChange">
      <div class="searchBar__numChangeBox__increaseBtn__icon">
        <IconPlus class="searchBar__numChangeBox__increaseBtn__icon__svg" />
      </div>
    </button>
  </div>
</template>

<style lang="scss" scoped>
.searchBar__numChangeBox__decreaseBtn__icon,
.searchBar__numChangeBox__increaseBtn__icon {
  display: inline-flex;
  align-self: center;
  top: 0.12em;
  pointer-events: none;
}
.searchBar__numChangeBox__decreaseBtn__icon__svg,
.searchBar__numChangeBox__increaseBtn__icon__svg {
  stroke: var(--color-text-gray2);
  height: 1em;
  width: fit-content;
}
.searchBar__numChangeBox {
  display: flex;
  flex-direction: row;
  align-items: center;
  height: 100%;
  width: 100%;
  padding: 0 2rem;
  background-color: var(--color-text-gray5);
}
input {
  -moz-appearance: textfield;
  text-align: center;
  font-family: montSB;
  font-size: 1.125rem;
  border: none;
  color: var(--color-text-white);
  background-color: transparent;
}
input:focus {
  outline: none;
}
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
button {
  color: var(--color-text-gray2);
  border: none;
  cursor: pointer;
}
#searchBar__numChangeBox__decreaseBtn,
#searchBar__numChangeBox__increaseBtn {
  text-align: center;
  font-family: monoSB;
  font-size: 1.125rem;
  background-color: transparent;
}
#searchBar__numChangeBox__decreaseBtn,
#searchBar__numChangeBox__increaseBtn {
  height: fit-content;
}
</style>
