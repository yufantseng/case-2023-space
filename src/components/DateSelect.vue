<script setup>
import { toRef, onMounted } from "vue";
import IconCalendar from "./icons/IconCalendar.vue";

const props = defineProps({
  type: {
    type: String,
    default: "",
  },
});
const type = toRef(props, "type");

onMounted(() => {
  const date_picker_element = document.querySelector(
    `.serchBar__dateSelectBox__dateSelect__${type.value}`
  );
  const selected_date_element =
    date_picker_element.querySelector(".selected__date");

  const dates_element = date_picker_element.querySelector(".dates");
  const mth_element = date_picker_element.querySelector(".mth");
  const next_mth_element = date_picker_element.querySelector(".next__mth");
  const prev_mth_element = date_picker_element.querySelector(".prev__mth");
  const days_element = date_picker_element.querySelector(".days");

  const months = [
    "January",
    "February",
    "March",
    "April",
    "May",
    "June",
    "July",
    "August",
    "September",
    "October",
    "November",
    "December",
  ];

  let date = new Date();
  let day = date.getDate();
  let month = date.getMonth();
  let year = date.getFullYear();

  let selectedDate = date;
  let selectedDay = day;
  let selectedMonth = month;
  let selectedYear = year;

  mth_element.textContent = months[month] + " " + year;

  selected_date_element.textContent = formatDate(date);
  selected_date_element.dataset.value = selectedDate;

  populateDates();

  // EVENT LISTENERS
  date_picker_element.addEventListener("click", toggleDatePicker);
  next_mth_element.addEventListener("click", goToNextMonth);
  prev_mth_element.addEventListener("click", goToPrevMonth);

  // FUNCTIONS
  function toggleDatePicker(e) {
    if (!checkEventPathForClass(e.composedPath(), "dates")) {
      dates_element.classList.toggle("active");
    }
  }

  function goToNextMonth() {
    month++;
    if (month > 11) {
      month = 0;
      year++;
    }
    mth_element.textContent = months[month] + " " + year;
    populateDates();
  }

  function goToPrevMonth() {
    month--;
    if (month < 0) {
      month = 11;
      year--;
    }
    mth_element.textContent = months[month] + " " + year;
    populateDates();
  }

  function populateDates() {
    days_element.innerHTML = "";
    let amount_days = 31;

    if (month == 1) {
      amount_days = 28;
    }

    for (let i = 0; i < amount_days; i++) {
      const day_element = document.createElement("div");
      day_element.classList.add("day");
      day_element.textContent = i + 1;

      if (
        selectedDay == i + 1 &&
        selectedYear == year &&
        selectedMonth == month
      ) {
        day_element.classList.add("selected");
      }

      day_element.addEventListener("click", function () {
        selectedDate = new Date(year + "-" + (month + 1) + "-" + (i + 1));
        selectedDay = i + 1;
        selectedMonth = month;
        selectedYear = year;

        selected_date_element.textContent = formatDate(selectedDate);
        selected_date_element.dataset.value = selectedDate;

        populateDates();
      });

      days_element.appendChild(day_element);
    }
  }

  // HELPER FUNCTIONS
  function checkEventPathForClass(path, selector) {
    for (let i = 0; i < path.length; i++) {
      if (path[i].classList && path[i].classList.contains(selector)) {
        return true;
      }
    }

    return false;
  }
  function formatDate(d) {
    let day = d.getDate();
    if (day < 10) {
      day = "0" + day;
    }

    let month = d.getMonth() + 1;
    if (month < 10) {
      month = "0" + month;
    }

    let year = d.getFullYear();

    return day + "." + month + "." + year;
  }
});
</script>

<template>
  <div class="serchBar__dateSelectBox">
    <div
      class="serchBar__dateSelectBox__dateSelect"
      :class="`serchBar__dateSelectBox__dateSelect__${type}`"
    >
      <span class="searchBar__dateSelectBox__icon">
        <IconCalendar class="searchBar__dateSelectBox__icon__svg" />
      </span>
      <div class="selected__date"></div>
      <div class="dates">
        <div class="month">
          <div class="arrows prev__mth">&lt;</div>
          <div class="mth"></div>
          <div class="arrows next__mth">&gt;</div>
        </div>
        <div class="days"></div>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.searchBar__dateSelectBox__icon {
  display: inline-flex;
  align-self: center;
  padding-right: 0.45rem;
}
.searchBar__dateSelectBox__icon__svg {
  stroke: var(--color-text-gray2);
  height: 1em;
  width: 1em;
}
.serchBar__dateSelectBox{
  height: 100%;
}
.serchBar__dateSelectBox__dateSelect {
  position: relative;
  width: max-content;
  font-family: montSB;
  text-transform: uppercase;
  padding: 0 1rem;
  display: inline-block;
  height: 100%;
  background-color: var(--color-text-gray5);
  cursor: pointer;
  user-select: none;
  align-items: center;
  font-size: 1.125rem;
  width: 100%;
  display: flex;
  flex-direction: row;
}
.serchBar__dateSelectBox__dateSelect .selected__date {
  color: var(--color-text-white);
}
.serchBar__dateSelectBox__dateSelect .dates {
  display: none;
  position: absolute;
  top: 100%;
  left: 0;
  right: 0;
  background-color: #fff;
}
.serchBar__dateSelectBox__dateSelect .dates.active {
  display: block;
}
.serchBar__dateSelectBox__dateSelect .dates .month {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-bottom: 2px solid #eee;
}
.serchBar__dateSelectBox__dateSelect .dates .month .arrows {
  width: 35px;
  height: 35px;
  display: flex;
  justify-content: center;
  align-items: center;
  color: #313131;
  font-size: 20px;
}
.serchBar__dateSelectBox__dateSelect .dates .month .arrows:hover {
  background-color: #f3f3f3;
}
.serchBar__dateSelectBox__dateSelect .dates .month .arrows:active {
  background-color: #00ca85;
}
.serchBar__dateSelectBox__dateSelect .dates .days {
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  height: 200px;
}
.serchBar__dateSelectBox__dateSelect .dates .days .day {
  display: flex;
  justify-content: center;
  align-items: center;
  color: #313131;
}
.serchBar__dateSelectBox__dateSelect .dates .days .day.selected {
  background-color: #00ca85;
}
</style>
