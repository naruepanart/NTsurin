<template>
  <div>  
    <p>คำตอบ อาชีพในอนาคต</p>
    <p>จำนวนคนส่ง : {{firstname.length}} คน</p>
    <hr>
       <tr v-for="firstnames, i in firstname">
         <p>ชื่อ : {{firstnames.firstname}} {{firstnames.lastname}}&nbsp;
           <button v-on:click="onDelete(firstnames._id,i)">Delete</button></p>
        <p>ห้อง : {{firstnames.classroom}} เลขที่ : {{firstnames.numberclassroom}}</p>
        <p>รายละเอียด : <br>{{firstnames.text}}</p>
      </tr>
  </div> 
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      firstname: "",
      lastname: "",
      classroom: "",
      numberclassroom: "",
      text: ""
    };
  },
  methods: {
    onDelete(id,i) {
      axios.delete(
        `https://api-surinsmartcity.herokuapp.com/nongtongsurawittayakom/futurecareer/` + id, {
          method: "DELETE"
        })
        .then(() => {
      this.firstname.splice(i, 1);
      //this.$delete(this.facebook, index)
    })
    }
  },
  mounted() {
    axios
      .get(
        `https://api-surinsmartcity.herokuapp.com/nongtongsurawittayakom/futurecareer/`
      )
      .then(response => {
        this.firstname = response.data;
        //console.log("Data : ", response.data);
      })
      .catch(function(error) {
        //console.log("Error : ", error);
      });
  }

  // Fetches firstname when the component is created.
  /*  mounted() {
    fetch(`https://apiwarpth-zcrbcgqtob.now.sh/firstname`)
      .then(response => response.json())
      .then(firstname => {
        this.firstname = firstname;
        // console.log(firstname);
      });
  } */
};
</script>


<style scoped>
button{
  background-color: red;
  border-radius: 0.25em;
  border: 1px solid red;
  color: #ffffff;
  font-size: 0.8em;
  padding: 0.6em;
  width: 20%;
}
</style>