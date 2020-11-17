<template>
  <section class="bar-section">
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
    <div class="bar-block">
      <span>Color</span>
      <input
          class="input"
          type="color"
          @change="fontBarChangeMethod('color', selectedColor)"
          v-model="selectedColor"
      />
<!--      <InputGroup-->
<!--          class="input"-->
<!--          :type="inputValues.colorInput.type"-->
<!--          :inputLabel="inputValues.colorInput.label"-->
<!--          @change="fontBarChangeMethod('color', selectedColor)"-->
<!--          v-model="selectedColor"-->
<!--      />-->
    </div>
    <div class="bar-block">
      <span>Background color</span>
      <input
          class="input"
          type="color"
          @change="fontBarChangeMethod('backgroundColor', selectedBackground)"
          v-model="selectedBackground"
      />
    </div>
  </section>
</template>

<script>
// import InputGroup from "@/components/formItems/InputGroup";
export default {
  name: 'EditableButtons',
  // components: {InputGroup},
  data() {
    return {
      selectedFontSize: "",
      selectedColor: "",
      selectedBackground: "",
      fontSizes: [
        { value: "14px", text: "14" },
        { value: "16px", text: "16" },
        { value: "30px", text: "30" },
        { value: "40px", text: "40" }
      ],
      inputValues: {
        colorInput: {
          type: 'color',
          label: 'Color'
        },
        backgroundColor: {
          type: 'color',
          label: 'Background color'
        }
      }
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
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.bar-block {
  margin-right: 30px;
}
.bar-block span {
  margin-right: 10px;
}
.bar-block:last-child {
  margin-right: 0;
}
.select {
  margin: 10px;
}
.input {
  width: 80px;
  height: 25px;
}
</style>
