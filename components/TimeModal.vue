<template>
  <div v-if="visible" class="modal-overlay">
    <div class="modal-content">
      <h3>Update Time {{ taskName }}</h3>
      <input type="datetime-local" v-model="datetimeInput" />
      <button @click="handleSubmit">Submit</button>
      <button @click="close">Cancel</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    visible: {
      type: Boolean,
      required: true,
    },
    currentValue: {
      type: String,
      default: "",
    },
    taskName: {
      type: String,
      default: "",
    },
  },
  data() {
    return {
      datetimeInput: "",
    }
  },
  computed: {
    formattedDatetime() {
      if (this.currentValue) {
        const date = new Date(this.currentValue)
        // Format the date to 'YYYY-MM-DDTHH:MM'
        return date.toISOString().slice(0, 16)
      } else {
        return ""
      }
    },
  },
  mounted() {
    // Set the default value for datetimeInput when the modal is mounted
    this.datetimeInput = this.formattedDatetime
  },
  methods: {
    close() {
      this.$emit("close")
    },
    handleSubmit() {
      this.$emit("submit", this.datetimeInput)
      this.close()
    },
  },
}
</script>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}
.modal-content {
  background: white;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}
button {
  margin-right: 10px;
  padding: 5px 10px;
  background-color: #4caf50;
  color: white;
  border: none;
  cursor: pointer;
}
button:hover {
  background-color: #45a049;
}
</style>
