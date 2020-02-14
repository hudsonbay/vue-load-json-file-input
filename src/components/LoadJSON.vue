<template>
  <div class="hello">
    <input type="file" @change="onFileSelected" />

    <p>{{ jsonResult }}</p>
  </div>
</template>

<script>
export default {
  name: "LoadJSON",

  data() {
    return {
      jsonResult: null
    };
  },
  methods: {
    onFileSelected(event) {
      let file = event.target.files[0];

      if (!file || file.type !== "application/json")
        return alert("Se debe cargar un JSON");

      // Credit: https://stackoverflow.com/a/754398/52160
      let reader = new FileReader();
      reader.readAsText(file, "UTF-8");

      reader.onload = evt => {
        let text = evt.target.result;
        try {
          this.jsonResult = JSON.parse(text);
        } catch (e) {
          alert("Se ha producido un error al cargar el JSON");
        }
      };
      reader.onerror = evt => {
        console.error(evt);
      };
    },
    onUpload() {}
  }
};
</script>
