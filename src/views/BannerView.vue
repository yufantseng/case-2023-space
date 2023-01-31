<script setup>
import DestSelect from "../components/DestSelect.vue";
import DateSelect from "../components/DateSelect.vue";
import NumInput from "../components/NumInput.vue";
</script>

<template>
  <div class="bannerSection">
    <div class="container">
      <div class="banner__titleBox">
        <h2 class="banner__subTitle">discover begins with</h2>
        <h1 class="banner__title">journey</h1>
      </div>
      <div class="banner__searchBar">
        <div class="banner__searchBar__destSelectBox">
          <div class="banner__searchBar__destSelectBox__pt">
            <h3 class="banner__searchBar__destSelectBox__pt__title">from</h3>
            <DestSelect dest="earth" />
          </div>
          <div class="banner__searchBar__destSelectBox__pt">
            <h3 class="banner__searchBar__destSelectBox__pt__title">to</h3>
            <DestSelect dest="mars" />
          </div>
        </div>
        <div class="banner__searchBar__dateSelectBox">
          <div class="banner__searchBar__dateSelectBox__pt">
            <h3 class="banner__searchBar__dateSelectBox__pt__title">
              outbound
            </h3>
            <DateSelect type="outbound" />
          </div>
          <div class="banner__searchBar__dateSelectBox__pt">
            <h3 class="banner__searchBar__dateSelectBox__pt__title">inbound</h3>
            <DateSelect type="inbound" />
          </div>
        </div>
        <div class="banner__searchBar__numInputBoxt">
          <div class="banner__searchBar__numInputBoxt__pt">
            <h3 class="banner__searchBar__numInputBoxt__pt__title">
              astronaut
            </h3>
            <NumInput />
          </div>
        </div>
        <button type="submit" class="banner__searchBar__submitBtn">
          search
        </button>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.bannerSection {
  background-image: url(../assets/img/banner.jpg);
  background-position: center;
  background-size: cover;
  width: 100%;
  min-height: 750px;
  display: flex;
  flex-direction: row;
  align-items: center;
}
.container {
  padding: 0 2rem;
  max-width: 1290px;
  width: 100%;
  margin: auto;
  display: flex;
  flex-direction: column;
}
.banner__titleBox {
  width: 100%;
}
.banner__subTitle,
.banner__title {
  color: var(--color-text-white);
  text-transform: uppercase;
  font-family: monoM;
  line-height: 0.8em;
}
.banner__subTitle {
  font-size: clamp(1rem, 2.5vw, 3rem);
  margin-bottom: 1.5rem;
}
.banner__title {
  font-size: clamp(2rem, 6vw, 7.5rem);
}
.banner__searchBar,
.banner__searchBar__destSelect,
.banner__searchBar__destSelectBox,
.banner__searchBar__dateSelectBox,
.banner__searchBar__numInputBoxt {
  display: flex;
  flex-direction: row;
}
.banner__searchBar {
  background-color: var(--vt-c-black);
  padding: 3.5rem 3rem;
}
.banner__searchBar__destSelectBox__pt,
.banner__searchBar__dateSelectBox__pt,
.banner__searchBar__numInputBoxt__pt {
  display: flex;
  flex-direction: column;
  width: 50%;
}
.banner__searchBar__destSelectBox__pt__title,
.banner__searchBar__dateSelectBox__pt__title,
.banner__searchBar__numInputBoxt__pt__title {
  width: 100%;
  font-size: 1.125rem;
  color: var(--vt-c-gray1);
  font-family: montL;
  text-transform: uppercase;
  padding: 0 1rem 0.75rem;
}
.banner__searchBar__destSelectBox {
  width: 30%;
}
.banner__searchBar__dateSelectBox {
  width: 40%;
}
.banner__searchBar__numInputBoxt {
  width: 30%;
}
.banner__searchBar__submitBtn {
  width: 20%;
  height: 100%;
  background-color: var(--vt-c-gray1);
}
</style>
