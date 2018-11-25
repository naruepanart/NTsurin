<template>
  <div>  
    <h2>คำตอบ Smart city</h2>
    <p>จำนวนคนส่ง : {{firstname.length}} คน</p>
       <tr v-for="firstnames, i in firstname">
         <p>ชื่อจริง : {{firstnames.firstname}}
           <button v-on:click="onDelete(firstnames._id,i)">Delete</button></p>
        <p>นามสกุล : {{firstnames.lastname}}</p>
        <p>ชั้นประถมศึกษาปีที่ : {{firstnames.classroom}}</p>
        <p>เลขที่ : {{firstnames.numberclassroom}}</p>
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
        `https://api-surinsmartcity.herokuapp.com/nongtongsurawittayakom/primaryschool/` + id, {
          method: "DELETE"
        })
        .then(() => {
      this.facebook.splice(i, 1);
      //this.$delete(this.facebook, index)
    })
    }
  },
  mounted() {
    axios
      .get(
        `https://api-surinsmartcity.herokuapp.com/nongtongsurawittayakom/primaryschool/`
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


