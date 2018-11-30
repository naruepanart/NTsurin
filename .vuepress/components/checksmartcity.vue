<template>
  <div> 
      <center> 
    <p>จำนวนคนส่ง : {{firstname.length}} คน</p>
     <td>ชื่อจริง</td>
     <td>นามสกุล</td>
      <td>ห้อง</td>
      <td>เลขที่</td>
       <tr v-for="firstnames in firstname">
         <td>{{firstnames.firstname}}</td> 
         <td>{{firstnames.lastname}}</td>
         <td>{{firstnames.classroom}}</td>
         <td>{{firstnames.numberclassroom}}</td>
      </tr>
        </center>
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
  mounted() {
    axios
      .get(
        `https://api-surinsmartcity.herokuapp.com/nongtongsurawittayakom/surinsmartcity/`
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
