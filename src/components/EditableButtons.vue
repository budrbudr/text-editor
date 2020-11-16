<template>
  <section class="bar-section">
    <div class="bar-block">
      <span>Color</span>
      <input
          class="color-input"
          type="color"
          @change="fontBarChangeMethod('color', selectedColor)"
          v-model="selectedColor"
      />
    </div>
    <div class="bar-block">
      <span>Background color</span>
      <input
          class="color-input"
          type="color"
          @change="fontBarChangeMethod('backgroundColor', selectedBG)"
          v-model="selectedBG"
      />
    </div>
    <div class="bar-block">
      <span>Font size</span>
      <select
          class="select"
          v-model="selectedFontSize"
          @change="fontBarChangeMethod('fontSize', selectedFontSize)"
      >
        <option
            v-for="size in fontSizes"
            :key="size.text"
            :value="size.value"
        >{{ size.text }}</option>
      </select>
    </div>
  </section>
</template>

<script>
export default {
  name: 'EditableButtons',
  data() {
    return {
      selectedFontSize: "",
      selectedColor: "",
      selectedBG: "",
      selected: 3,
      fontSizes: [
        { value: "14px", text: "14" },
        { value: "16px", text: "16" },
        { value: "30px", text: "30" },
        { value: "40px", text: "40" }
      ]
    };
  },
  methods: {
    fontBarChangeMethod(param, value) {
      const range = window.getSelection().getRangeAt(0);
      const span = document.createElement("span");
      span.style[param] = value;
      span.appendChild(range.extractContents());
      range.insertNode(span);
    },
  }
};
</script>

<style scoped>
.bar-section {
  text-align: center;
  margin: 20px auto;
  max-width: 500px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.bar-block {
  margin-right: 30px;
}
.bar-block:last-child {
  margin-right: 0;
}
.select {
  margin: 10px;
}
.color-input {
  width: 50px;
  height: 20px;
}
</style>
