<template>
  <div>
    <p>จำนวนคนส่ง : {{firstname.length}} คน</p>
    <td>ชื่อ</td>
    <td>นามสกุล</td>
    <td>ห้อง</td>
    <td>เลขที่</td>
    <tr v-for="firstnames in firstname">
      <td>{{firstnames.titlename}}{{firstnames.firstname}}</td>
      <td>{{firstnames.lastname}}</td>
      <td>{{firstnames.classroom}}</td>
      <td>{{firstnames.numberclassroom}}</td>
    </tr>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      titlename: "",
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
td {
  border: none;
}
</style>