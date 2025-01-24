<script setup lang="ts">
import { computed, onMounted } from "vue";
import InputText from "./settings/InputText.vue";
import ColorButton from "./settings/ColorButton.vue";
import SettingsSection from "./SettingsSection.vue";
import offices from "../data/offices.json";
import kana from "../data/kana.json";

const model = defineModel();

const checkValiditySerial = (event) => {
  if (event.target.value.match(/^\d{0,4}$/))
    model.value.serial = event.target.value;
};

const checkValidityClassification = (event) => {
  if (event.target.value.match(/^\d{0,4}$/))
    model.value.classification = event.target.value;
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

const formattedKana = computed(() => {
  const output = kana.private.map((kana) => ({
    value: kana.kana,
    text: `${kana.kana} - ${kana.transliteration}`,
  }));

  const specialoutput = kana.special.map((character) => ({
    value: character,
    text: character,
  }));

  return [...output, ...specialoutput];
});
</script>

<template>
  <div
    class="flex flex-col overflow-hidden rounded-2xl bg-white *:p-4 dark:bg-gray-700"
  >
    <h1 class="text-center text-xl">JDM Plate generator</h1>
    <p class="p-4">
      {{ model }}
    </p>
    <div class="scrollbar-thin overflow-auto border-y dark:border-gray-800">
      <SettingsSection title="Color">
        <div class="flex">
          <ColorButton
            v-model="model.color"
            value="regular"
            name="color"
            background="#d7d8d5"
            foreground="#194a17"
          />
          <ColorButton
            v-model="model.color"
            value="kei"
            name="color"
            background="#f1c209"
            foreground="#000"
          />
          <ColorButton
            v-model="model.color"
            value="commercial"
            name="color"
            background="#194a17"
            foreground="#d7d8d5"
          />
          <ColorButton
            v-model="model.color"
            value="commercial-kei"
            name="color"
            background="#000"
            foreground="#f1c209"
          />
        </div>
      </SettingsSection>
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
      <SettingsSection title="Vehicle classification">
        <InputText
          :model-value="model.classification"
          maxlength="3"
          pattern="[0-9]{3}"
          @input="checkValidityClassification($event)"
        />
      </SettingsSection>
      <SettingsSection title="Kana">
        <select v-model="model.kana">
          <option
            v-for="kana in formattedKana"
            :value="kana.value"
            :key="kana.value"
          >
            {{ kana.text }}
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
