<script setup>
import { ref, toRef, onMounted } from "vue";
import IconEarth from "../components/icons/IconEarth.vue";
import IconMars from "../components/icons/IconMars.vue";
const planets = ref([
  "earth",
  "mars",
  "mercury",
  "venus",
  "jupiter",
  "saturn",
  "uranus",
  "neptune",
]);
const props = defineProps({
  dest: {
    type: String,
    default: "",
  },
});
const dest = toRef(props, "dest");
function iconChange() {
  switch (dest.value) {
    case "earth":
      return IconEarth;
    case "mars":
      return IconMars;
    default:
      return null;
  }
}
onMounted(() => {
  let x, i, j, l, ll, selElmnt, a, b, c;
  x = document.getElementsByClassName(
    `searchBar__selectBox__select-${dest.value}`
  );
  l = x.length;
  for (i = 0; i < l; i++) {
    selElmnt = x[i].getElementsByTagName("select")[0];
    ll = selElmnt.length;
    /*for each element, create a new DIV that will act as the selected item:*/
    a = document.createElement("DIV");
    a.setAttribute("class", "searchBar__selectBox__select-selected");
    a.innerHTML = selElmnt.options[selElmnt.selectedIndex].innerHTML;
    x[i].appendChild(a);
    /*for each element, create a new DIV that will contain the option list:*/
    b = document.createElement("DIV");
    b.setAttribute(
      "class",
      "searchBar__selectBox__select-items searchBar__selectBox__select-hide"
    );
    for (j = 1; j < ll; j++) {
      /*for each option in the original select element,
      create a new DIV that will act as an option item:*/
      c = document.createElement("DIV");
      c.innerHTML = selElmnt.options[j].innerHTML;
      c.addEventListener("click", function (e) {
        /*when an item is clicked, update the original select box,
          and the selected item:*/
        let y, i, k, s, h, sl, yl;
        s = this.parentNode.parentNode.getElementsByTagName("select")[0];
        sl = s.length;
        h = this.parentNode.previousSibling;
        for (i = 0; i < sl; i++) {
          if (s.options[i].innerHTML == this.innerHTML) {
            s.selectedIndex = i;
            h.innerHTML = this.innerHTML;
            y = this.parentNode.getElementsByClassName(
              "searchBar__selectBox__select-same-as-selected"
            );
            yl = y.length;
            for (k = 0; k < yl; k++) {
              y[k].removeAttribute("class");
            }
            this.setAttribute(
              "class",
              "searchBar__selectBox__select-same-as-selected"
            );
            break;
          }
        }
        h.click();
      });
      b.appendChild(c);
    }
    x[i].appendChild(b);
    a.addEventListener("click", function (e) {
      /*when the select box is clicked, close any other select boxes,
        and open/close the current select box:*/
      e.stopPropagation();
      closeAllSelect(this);
      this.nextSibling.classList.toggle("searchBar__selectBox__select-hide");
    });
  }
  function closeAllSelect() {
    /*a function that will close all select boxes in the document,
    except the current select box:*/
    let x,
      i,
      xl,
      arrNo = [];
    x = document.getElementsByClassName("searchBar__selectBox__select-items");
    xl = x.length;
    for (i = 0; i < xl; i++) {
      if (arrNo.indexOf(i)) {
        x[i].classList.add("searchBar__selectBox__select-hide");
      }
    }
  }
  document.addEventListener("click", closeAllSelect);
});
</script>

<template>
  <div class="searchBar__selectBox">
    <div
      :class="`searchBar__selectBox__select-${dest}`"
      class="searchBar__selectBox__select"
    >
      <select>
        <template v-for="(planet, i) in planets" :key="i">
          <option v-if="planet != dest" :value="i">
            <span class="searchBar__selectBox__select__icon">
              <component
                class="searchBar__selectBox__select__icon__svg"
                :is="iconChange()"
              ></component>
            </span>
            {{ planet }}
          </option>
        </template>
      </select>
    </div>
  </div>
</template>

<style lang="scss">
.searchBar__selectBox__select__icon {
  display: inline-flex;
  align-self: center;
  top: 0.12em;
  padding-right: 0.1rem;
}
.searchBar__selectBox__select__icon__svg {
  fill: var(--color-text-gray2);
  height: 1em;
  width: 1em;
}
.searchBar__selectBox {
  display: flex;
  flex-direction: row;
  width: 100%;
}
.searchBar__selectBox__select {
  position: relative;
  font-family: montSB;
  text-transform: uppercase;
  height: 100%;
  width: 100%;
}
.searchBar__selectBox__select select {
  display: none;
}
.searchBar__selectBox__select-selected {
  background-color: var(--color-text-gray5);
}
/*style the items (options), including the selected item:*/
.searchBar__selectBox__select-items div,
.searchBar__selectBox__select-selected {
  color: var(--color-text-white);
  padding: 1.375rem 1rem;
  cursor: pointer;
  user-select: none;
  font-size: 1.125rem;
}
/*style items (options):*/
.searchBar__selectBox__select-items {
  position: absolute;
  background-color: var(--color-text-gray5);
  top: 100%;
  left: 0;
  right: 0;
  z-index: 99;
}
.searchBar__selectBox__select-hide {
  display: none;
}
</style>
