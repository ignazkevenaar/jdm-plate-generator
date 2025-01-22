<script setup lang="ts">
import { computed, onMounted } from "vue";
import InputText from "./settings/InputText.vue";
import SettingsSection from "./SettingsSection.vue";
import offices from "../data/offices.json";

const model = defineModel();

const checkValiditySerial = (event) => {
  if (event.target.value.match(/^\d{0,4}$/))
    model.value.serial = event.target.value;
};

const formattedOffices = computed(() =>
  offices.flatMap((prefecture) =>
    prefecture.municipalities.flatMap((municipality) =>
      municipality.markings.flatMap((marking) => ({
        value: marking.international,
        text: `${prefecture.transliteration} - ${municipality.name} - ${marking.transliteration} / ${marking.kanji}`,
      })),
    ),
  ),
);
</script>

<template>
  <div
    class="flex flex-col overflow-hidden rounded-2xl bg-white *:p-4 dark:bg-gray-700"
  >
    <h1 class="text-center text-xl">JDM Plate generator</h1>
    <div class="scrollbar-thin overflow-auto border-y dark:border-gray-800">
      <SettingsSection title="Serial number">
        <InputText
          :model-value="model.serial"
          maxlength="4"
          pattern="[0-9]{4}"
          @input="checkValiditySerial($event)"
        />
      </SettingsSection>
      <SettingsSection title="Office">
        <select v-model="model.office">
          <option
            v-for="office in formattedOffices"
            :value="office.value"
            :key="office.value"
          >
            {{ office.text }}
          </option>
        </select>
      </SettingsSection>
    </div>
    <div class="text-center">
      <button
        class="rounded-full bg-purple-600 px-8 py-2 text-lg font-bold capitalize text-white"
      >
        generate
      </button>
    </div>
  </div>
</template>
