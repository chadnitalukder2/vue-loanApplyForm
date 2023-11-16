<template>
  <div class="modal">
    <div class="modal-box">
      <h1>Hi Iam Modal</h1>
      <button @click="close" class="btn">click me</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "A_model",
  methods: {
    close() {
      this.$emit("close");
    },
  },
};
</script>

<style lang="scss" scoped>
.modal {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.3);
  display: flex;
  justify-content: center;
  align-items: center;
}
.modal-box {
  background: white;
  padding: 20px;
  border-radius: 5px;
  box-shadow: 2px 1px 12px black;
}
.btn {
  margin: 30px 50px 0px 50px;
  padding: 8px;
  font-size: 16px;
  background: black;
  color: #fff;
  border: 2px solid rgb(187, 184, 184);
}
</style>
