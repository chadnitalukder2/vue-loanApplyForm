<template>
  <button class="btn" @click="showModal">Add Detail</button>
  <Form @submited="submited" v-show="isModalVisible" />
  <Table :details="details" @DeleteItem="DeleteBtn" :grentTotal="grentTotal" />
  <!-- <Modal v-show="isModalVisible" @close="closeModl"/> -->
</template>

<script>
//import Modal from './components/A_model.vue'
import Form from "./components/A_from.vue";
import Table from "./components/A_Table.vue";

export default {
  name: "App",
  components: {
    //Modal,
    Form,
    Table,
  },
  data() {
    return {
      details: [],
      grentTotal: 0,
      isModalVisible: false,
    };
  },
  methods: {
    showModal() {
      this.isModalVisible = true;
    },
    closeModl() {
      this.isModalVisible = false;
    },
    submited(detailsItem) {
      this.isModalVisible = false;
      if (
        detailsItem.date == "" ||
        detailsItem.fullName == "" ||
        detailsItem.address == "" ||
        detailsItem.number == "" ||
        detailsItem.email == "" ||
        detailsItem.birth == "" ||
        detailsItem.gender == "" ||
        detailsItem.type == "" ||
        detailsItem.amount == "" ||
        detailsItem.description == ""
      ) {
        alert("Plase fill the from");
        return;
      }
      let data = {
        date: detailsItem.date,
        fullName: detailsItem.fullName,
        address: detailsItem.address,
        number: detailsItem.number,
        email: detailsItem.email,
        birth: detailsItem.birth,
        gender: detailsItem.gender,
        type: detailsItem.type,
        amount: detailsItem.amount,
        description: detailsItem.description,
      };
      console.log(data, "hoi");
      this.details?.push(data);

      this.calculateTotal();
      this.saveToLocalStorage();
    },

    DeleteBtn(index) {
      this.details = this.details.filter((data, Toindex) => Toindex != index);
      this.calculateTotal();
      this.saveToLocalStorage();
    },
    calculateTotal() {
      let sum = 0;
      for (let i = 0; i < this.details?.length; i++) {
        sum += Number(this.details[i].amount);
      }
      this.grentTotal = sum;
      this.saveToLocalStorage();
    },
    saveToLocalStorage() {
      localStorage.setItem("details", JSON.stringify(this.details));
    },
  },
  mounted() {
    this.details = JSON.parse(localStorage.getItem("details"));

    this.calculateTotal();
  },
};
</script>

<style lang="scss">
.btn {
  padding: 10px 20px;
  font-size: 18px;
  margin-left: 50%;
  margin-top: 40px;
  margin-bottom: 20px;
  border: 2px solid rgb(147 167 187 / 61%);
  background: #86b7fe;
  color: #333;
  transition: 0.2s;
  border-radius: 5px;
  &:hover {
    border: 2px solid #86b7fe;
    background: #3b7cdd;
    color: #fff;
  }
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "popines", sans-serif;
}
.app {
  width: 100%;
  margin: 0 auto;
  max-width: 80%;
  margin-top: 20px;
  text-align: center;
  border-radius: 5px;
  background: rgb(248, 248, 248);
}
.container {
  h1 {
    padding: 20px;
    font-size: 30px;
    color: #333;
    @media only screen and (max-width: 576px) {
      font-size: 18px;
    }
  }
}
</style>
