<script setup>
import DestSelect from "../components/DestSelect.vue";
import DateSelect from "../components/DateSelect.vue";
import NumInput from "../components/NumInput.vue";
import IconScrollDownArrow from "../components/icons/IconScrollDownArrow.vue";
</script>

<template>
  <section class="bannerSection">
    <div class="container">
      <div class="banner__titleBox">
        <h2 class="banner__subTitle">discover begins with</h2>
        <h1 class="banner__title">journey</h1>
      </div>
      <div class="banner__searchBar">
        <div class="banner__searchBar__titleBox">
          <h3 class="banner__searchBar__titleBox__title">
            Book your flight to the Stars
          </h3>
          <div class="banner__searchBar__titleBox__icon">
            <IconScrollDownArrow
              class="banner__searchBar__titleBox__icon__svg"
            />
          </div>
        </div>
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
  </section>
</template>

<style lang="scss" scoped>
.bannerSection {
  position: relative;
  background-image: url(../assets/img/banner.jpg);
  background-position: center;
  background-size: cover;
  width: 100%;
  min-height: 750px;
  display: flex;
  flex-direction: row;
  align-items: center;
}
.banner__searchBar__titleBox {
  position: absolute;
  width: calc(100% - 6rem);
  display: flex;
  flex-direction: column;
  align-items: center;
  top: -40%;
}
.banner__searchBar__titleBox__title {
  font-family: monoR;
  font-size: 1.5rem;
  color: var(--color-text-white);
}
.banner__searchBar__titleBox__icon {
  display: inline-flex;
  align-self: center;
  top: 0.5rem;
}
.banner__searchBar__titleBox__icon__svg {
  stroke: var(--color-text-white);
  height: 2rem;
  width: fit-content;
}
.container {
  padding: 0 2rem;
  max-width: 1290px;
  width: 100%;
  margin: 10% auto auto;
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
  margin-bottom: 3rem;
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
  position: absolute;
  width: 100%;
  top: 270%;
  background-color: var(--vt-c-black);
  padding: 3.5rem 3rem;
  background: linear-gradient(0deg, var(--vt-c-black), var(--vt-c-black)),
    radial-gradient(
      95.81% 95.81% at 50% 57.76%,
      rgba(6, 18, 46, 1) 17.19%,
      rgba(160, 186, 249, 0) 100%,
      rgba(24, 139, 186, 0.06) 100%
    );
  box-shadow: 10px 5px 107px 20px rgba(20, 136, 184, 0.4);
}
.banner__searchBar__destSelectBox__pt,
.banner__searchBar__dateSelectBox__pt,
.banner__searchBar__numInputBoxt__pt {
  display: flex;
  flex-direction: column;
  width: 100%;
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
  margin-right: 1.5rem;
}
.banner__searchBar__dateSelectBox {
  width: 40%;
  margin-right: 1.5rem;
}
.banner__searchBar__numInputBoxt {
  width: 15%;
  margin-right: 1.5rem;
}
.banner__searchBar__submitBtn {
  width: 15%;
  color: var(--color-text-white);
  background-color: var(--vt-c-gray5);
  text-transform: uppercase;
  font-family: montSB;
  font-size: 1.125rem;
  outline: none;
  border: none;
  cursor: pointer;
  margin-top: 2.125rem;
  padding: 0;
}
</style>
