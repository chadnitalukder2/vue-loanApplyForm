<template>
  <Form @submited="submited" />
  <Table :details="details" @DeleteItem="DeleteBtn" :grentTotal="grentTotal" />
</template>

<script>
import Form from './components/A_from.vue';
import Table from './components/A_Table.vue'

export default {
  name: 'App',
  components: {
    Form,
    Table
  },
  data(){
    return{
      details:JSON.parse(localStorage.getItem("details")) || [],
      grentTotal: 0
    }
  },
  methods:{

    submited(detailsItem){
if(
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
){
alert ("Plase fill the from");
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
            description: detailsItem.description
};
console.log(detailsItem, "not found");
this.details.push(data);
 this.calculateTotal();
this.saveToLocalStorage()
console.log(this.details,"hi");
    },

DeleteBtn(index){
  this.details = this.details.filter((data, Toindex) => Toindex != index)
  this.calculateTotal();
  this.saveToLocalStorage()
},
calculateTotal() {
      let sum = 0;
      for (let i = 0; i < this.details.length; i++) {
        sum += Number(this.details[i].amount);
      }
      this.grentTotal = sum;
      this.saveToLocalStorage();
    },
saveToLocalStorage() {
      localStorage.setItem("details", JSON.stringify(this.details));
    },
  },
  mounted(){
  
this.details = JSON.parse(localStorage.getItem("details"));
this.calculateTotal();
  }

}
</script>

<style lang="scss">
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
