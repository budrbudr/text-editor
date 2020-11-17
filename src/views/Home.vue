<template>
    <main>
        <h1>Text Editor</h1>
        <section class="content-section">
            <EditableButtons/>
            <Editor @input="textEl = $event"/>
        </section>
    </main>
</template>

<script>
    import Editor from "../components/Editor";
    import EditableButtons from "@/components/EditableButtons";

    export default {
        name: "Home",
        components: {EditableButtons, Editor},
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
