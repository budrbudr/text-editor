<template>
    <section>
        <button class="btn btn-primary" type="button" @click="converterToJson">
            Convert to Json
        </button>
    </section>
</template>

<script>
    export default {
        name: "JsonConverter",
        methods: {
            converterToJson() {
                let json = {
                    textNodes: []
                };
                let childNodes = this.$refs.div.childNodes;
                childNodes.forEach(child => {
                    if (child.nodeName === "#text") {
                        json.textNodes.push({
                            text: child.nodeValue,
                            color: "#000",
                            backColor: "#fff",
                            fontSize: "14px"
                        });
                    } else {
                        json.textNodes.push({
                            text: child.textContent,
                            color: child.style.color ? child.style.color : "#000",
                            backColor: child.style.backgroundColor
                                ? child.style.backgroundColor
                                : "#fff",
                            fontSize: child.style.fontSize ? child.style.fontSize : "14px"
                        });
                    }
                });
                console.log(json);
            }
        }
    }
</script>

<style scoped>

</style>
