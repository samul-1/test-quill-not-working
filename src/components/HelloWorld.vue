<template>
  <quill-editor
    :options="editorOptions"
    :value="modelValue"
    @change="onEditorChange($event)"
  />
</template>

<script>
import { defineComponent } from "@vue/runtime-core";
import { quillEditor } from "vue3-quill";
export default defineComponent({
  name: "TextEditor",
  props: {
    modelValue: {
      type: String,
      required: true,
    },
  },
  components: {
    quillEditor,
  },
  methods: {
    onEditorChange({ html }) {
      this.$emit("update:modelValue", html);
    },
  },
  computed: {
    editorOptions() {
      return {
        theme: "snow",
        modules: {
          toolbar: [
            ["bold", "italic", "underline", "strike"],
            ["code-block"],
            [{ list: "ordered" }, { list: "bullet" }],
            ["image"],
          ],
        },
      };
    },
  },
});
</script>
