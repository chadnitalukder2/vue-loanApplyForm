<template>
  <div class="app">
    <div class="container">
      <h1>LOAN APPLICATION FORM</h1>
      <form>
        <div class="box">
          <div class="left">
            <div class="box-1">
              <label>Date :</label>
              <input type="date" v-model="detailsItem.date" /><br /><br />
            </div>

            <div class="box-1">
              <label>FullName :</label>
              <input
                type="text"
                v-model="detailsItem.fullName"
                placeholder="enter your fullname"
              /><br /><br />
            </div>

            <div class="box-1">
              <label>Address :</label>
              <input type="text" v-model="detailsItem.address" placeholder="enter your address" /><br /><br />
            </div>

            <div class="box-1">
              <label>Number :</label>
              <input type="text" v-model="detailsItem.number" placeholder="enter your number" /><br /><br />
            </div>
            <div class="box-1">
              <label>Email :</label>
              <input type="email" v-model="detailsItem.email" placeholder="enter your email" /><br /><br />
            </div>
    
          </div>

          <div class="right">
            <div class="box-2">
              <label>Gender : </label><br /><br />
              <input type="radio" v-model="detailsItem.gender" value="Male"  />
              <label> Male</label><br />
              <input type="radio" v-model="detailsItem.gender" value="Female"  />
              <label> Female</label><br />
              <input type="radio" v-model="detailsItem.gender" value="Other"  />
              <label> Other</label><br /><br />
            </div>

            <div class="box-1">
             
              <label>Date Of Birth :</label>
              <input type="date" v-model="detailsItem.birth" /><br /><br />
            </div>


            <div class="box-3">
              
              <label >Type Of Business : </label>
              <select v-model="detailsItem.type" >
                <option value="Corporation">Corporation</option>
                <option value="Partnership">Partnership</option>
                <option value="Proprietorship">Proprietorship</option>
                <option value="Public">Public</option>
                <option value="Private">Private</option>
                <option value="Other">Other</option></select
              ><br /><br />
            </div>

            <div class="box-1">
              <label>Loan Amount : </label>
              <input type="text" v-model="detailsItem.amount" placeholder="enter loan amount" />
            </div>
            <div class="description">
          <label>Description :</label>
          <textarea v-model="detailsItem.description" placeholder="description..." rows="3" cols="50"></textarea>
        </div>
          </div>
        </div>
      
      </form>

      <button @click="submited()">Submit</button>
    </div>
  </div>
</template>

<script>
export default {
    name:"A_from",
    data(){
        return{
          detailsItem:{
            date: "",
            fullName:"",
            address:"",
            number:"",
            email:"",
            birth:"",
            gender:"",
            type:"",
            amount:"",
            description:"",
          },
        }
    },
    methods:{
        submited(){
            this.$emit('submited',this.detailsItem);
            console.log(this.detailsItem , "submited");
            this.detailsItem.date = "" ,
            this.detailsItem.fullName = "" 
            this.detailsItem.address = "" 
            this.detailsItem.number = "" 
            this.detailsItem.email = "" 
            this.detailsItem.birth = "" 
            this.detailsItem.gender = "" 
            this.detailsItem.type = "" 
            this.detailsItem.amount = "" 
            this.detailsItem.description = "" 
        },
          
    }
};
</script>

<style lang="scss" scoped>

form {
  padding: 50px;
  .box {
    display: flex;
    justify-content: space-between;
    text-align: start;
    gap: 100px;
    @media only screen and (max-width: 576px) {
        flex-wrap: wrap;
        gap: 15px
      }
 
    .left {
      flex-basis: 50%;
      @media only screen and (max-width: 576px) {
        flex-basis: 100%;
      }
    }

    .right {
      flex-basis: 50%;
      @media only screen and (max-width: 576px) {
        flex-basis: 100%;
      }
    }
    .box-1 {
      flex-basis: 45%;
      gap: 5%;
      margin: 10px 0;

      @media only screen and (max-width: 576px) {
        flex-basis: 100%;
      }

      label {
        font-size: 18px;
        color: #333;
      }

      input {
        margin-top: 12px;
        padding: 5px;
        border: none;
        border-bottom: 2px solid rgb(147 167 187 / 61%);
        line-height: 1.7em;
        width: 100%;
        font-size: 16px;
        font-weight: 400;
        background: transparent;

        &:focus-visible {
          outline: none;
          border-bottom: 2px solid #86b7fe;

          outline: 0;
        }
      }
    }
    .box-2 {
      label {
        font-size: 18px;
        color: #333;
      }
      input {
        margin: 6px;
      }
    }
    .box-3 {
      select {
        padding: 8px;
        border: 1px solid rgb(147 167 187 / 61%);
        font-size: 16px;
        &:focus-visible {
        outline: none;
        border: 1px solid #86b7fe;
        outline: 0;
      }
      }
    }

    .description {
    label {
      font-size: 18px;
      color: #333;
    }
    textarea {
        border-radius: 5px;
      padding: 10px;
      border: none;
      width: 100%;
      margin-top: 15px;
      border: 2px solid rgb(147 167 187 / 61%);
      &:focus-visible {
        outline: none;
        border: 2px solid #86b7fe;

        outline: 0;
      }
    }
  }
  }
  
}

button{
    padding: 10px 20px;
    font-size: 18px;
    margin-bottom: 20px;
    border: 2px solid rgb(147 167 187 / 61%);
    background: #86b7fe;
    color: #333;
    transition: 0.2s;
    border-radius: 5px;
    &:hover{
        border: 2px solid #86b7fe;
        background: #3b7cdd;
        color: #fff;
    }
}

</style>
