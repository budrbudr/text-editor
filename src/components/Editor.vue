<template>
  <section class="editor-section">
    <div
        contenteditable="true"
        class="editor"
        @input="update"
        ref="textarea"
    >
    </div>
    <div class="buttons-block">
      <h4 class="text-center">Console.log</h4>
      <button class="btn btn-primary" type="button" @click="converterToJson">
        Convert to Json
      </button>
    </div>
  </section>

</template>

<script>

export default {
  name: "Editor",
  methods: {
    update() {
      this.$emit("input", this.$el);
    },
    converterToJson() {
      let json = {
        textNodes: []
      };
      let childNodes = this.$refs.textarea.childNodes;
      childNodes.forEach(child => {
        if (child.nodeName === "#text") {
          json.textNodes.push({
            text: child.nodeValue,
            color: "#150707",
            backColor: "#f3e5e5",
            fontSize: "14px"
          });
        } else {
          json.textNodes.push({
            text: child.textContent,
            color: child.style.color ? child.style.color : "#150707",
            backColor: child.style.backgroundColor
                ? child.style.backgroundColor
                : "#f3e5e5",
            fontSize: child.style.fontSize ? child.style.fontSize : "14px"
          });
        }
      });
      console.log(json);
    }
  },

}
</script>

<style scoped>
.editor-section {
  display: flex;
  flex-direction: column;
  align-items: center;

}
.editor {
  width: 800px;
  height: 500px;
  border: 1px solid black;
}
.buttons-block {
  margin-top: 20px;
}
</style>
