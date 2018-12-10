<template>
  <div>
    <p>จำนวนคนส่ง : {{firstnames.length}} คน</p>
   
    <td>ชื่อ</td>
    <td>นามสกุล</td>
    <td>ห้อง</td>
    <td>เลขที่</td>
    <tr v-for="firstname,i in firstnames">
    
      <td>{{firstname.titlename}}{{firstname.firstname}}</td>
      <td>{{firstname.lastname}}</td>
      <td>{{firstname.classroom}}</td>
      <td>{{firstname.numberclassroom}}</td>
    </tr>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      titlename: "",
      firstnames: "",
      lastname: "",
      classroom: "",
      numberclassroom: ""
    };
  },
  mounted() {
    axios
      .get(
        `https://newapi-ntsurin.herokuapp.com/futurecareer/`
      )
      .then(response => {
        this.firstnames = response.data;
        //console.log("Data : ", response.data);
      });
  }

  // Fetches firstnames when the component is created.
  /*  mounted() {
    fetch(`https://apiwarpth-zcrbcgqtob.now.sh/firstnames`)
      .then(response => response.json())
      .then(firstnames => {
        this.firstnames = firstnames;
        // console.log(firstnames);
      });
  } */
};
</script>

<style scoped>
td {
  border: none;
}
</style>
