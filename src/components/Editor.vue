<template>
    <div
        contenteditable="true"
        class="editor"
        @input="update"
        >
    </div>
</template>

<script>

    export default {
        name: "Editor",
        methods: {
          update() {
            this.$emit("input", this.$el);
          },
        },

    }
</script>

<style scoped>
    .editor {
        width: 80%;
        height: 500px;
        border: 1px solid black;
    }
</style>
