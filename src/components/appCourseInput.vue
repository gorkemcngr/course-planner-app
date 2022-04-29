<template>
    <div class="card">
        <div class="user--action--container">
          <div class="form-group">
            <label>Kursun Adı</label>
            <input  v-model="newCourse" @keydown.enter="addCourse" type="text" />
          </div>
          <button @click="addCourse()" class="btn-primary">Kurs Ekle</button>
        </div>
      </div>
</template>
<script>
export default {
  data() {
    return {
      newCourse: null
    }
  },
  methods: {
    addCourse(){
      this.$emit("new-item", this.newCourse);
    }
  },
}
</script>