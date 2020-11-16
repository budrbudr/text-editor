<template>
    <main>
        <h1>Text Editor</h1>
        <section>
            <JsonConverter />
        </section>
        <section class="content-section">
            <EditableButtons/>
            <Editor @input="textEl = $event"/>
        </section>
    </main>
</template>

<script>
    import Editor from "../components/Editor";
    import EditableButtons from "@/components/EditableButtons";
    import JsonConverter from "../components/JsonConverter";

    export default {
        name: "Home",
        components: {JsonConverter, EditableButtons, Editor},
        methods: {},
    }
</script>

<style scoped>
    .content-section {
        display: flex;
        flex-direction: column;
        align-items: center;

    }

    h1 {

        text-align: center;
    }

</style>
