<template>
    <div class="app">
        <div class="container ">
            <h1>Table</h1>
            <table>
    <tr>
      <th>Date</th>
      <th>FulleName</th>
      <th>Address </th>
      <th>Number </th>
      <th>Date Of Birth</th>
      <th>Gender </th>
      <th>Type Of Business  </th>
      <th>Loan Amount </th>
      <th>Description </th>
      <th>..</th>
    </tr>
    <tr v-for="(detail,index) in details" :key="index">
   <td>{{detail.date}}</td>
   <td>{{detail.fullName}}</td>
   <td>{{detail.address}}</td>
   <td>{{detail.number}}</td>
   <td> {{detail.birth}}</td>
   <td>{{detail.gender}}</td>
   <td>{{detail.type}}</td>
   <td>{{detail.amount}}</td>
   <td>{{detail.description}}</td>
      <td>
        <button @click="DeleteBtn(index)" class="delete">Delete</button>
        <button class="edit">Edit</button>
      </td>
    </tr>
  
  </table>
  <h1>Total amount = {{ grentTotal }}</h1>
        </div>
    </div>
</template>

<script>
    export default {
        name:"A_table",
        props:[
            'details',
            'grentTotal'
        ],
        methods:{
            DeleteBtn(index){
                this.$emit("DeleteItem",index)
            }
        }
    }
</script>

<style lang="scss" scoped>
table {
  margin-top: 50px;
  margin-bottom: 100px;
  border-spacing: 0;
  width: 100%;
}

th,
td,
tr {
  padding: 10px 15px;
  border: 2px solid rgb(147 167 187 / 61%);
}

th {
  background: #86b7fe;
  color: #333;
  text-align: center;
}

table,
th,
td {
  border: 2px solid rgba(147, 167, 187, 0.61);
  border-collapse: collapse;
}

tr:nth-child(odd) td {
  background: rgba(33, 37, 41, 0.07);
}

.delete {
  background: orange;
  font-size: 13px;
  margin-bottom: 5px;
  padding: 6px 3px;
  border-radius: 5px;
  border: 1px solid rgba(147, 167, 187, 0.61);
}

.edit {
  background: #86b7fe;
  font-size: 13px;
  padding: 6px 10px;
  border-radius: 5px;
  border: 1px solid rgba(147, 167, 187, 0.61);
}


</style>