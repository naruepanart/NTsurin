<template>
  <div>  
    <h3>คำตอบ</h3>
    <p>จำนวนคนส่ง : {{firstname.length}} คน</p>
       <tr v-for="firstnames in firstname">
        <ul>ชั้นประถมศึกษาปีที่ : {{firstnames.classroom}} &nbsp;&nbsp;&nbsp;&nbsp;
          <button type="button" @click.once="onDelete(firstnames._id)">Delete</button></ul>
        <ul>เลขที่ : {{firstnames.numberclassroom}}</ul>
        <ul>ชื่อจริง : {{firstnames.firstname}}</ul>
        <ul>นามสกุล : {{firstnames.lastname}}</ul>
        <ul>รายละเอียด : <br>{{firstnames.text}}</ul>
      </tr>
  </div> 
</template>

<script>
import axios from "axios";
export default {
   data() {
    return {
      firstname: '',
      lastname: '',
      classroom: '',
      numberclassroom: '',
      text: ''
    };
  },
  methods: {
    onDelete(id) {
      axios.delete(
        `https://api-surinsmartcity.herokuapp.com/nongtongsurawittayakom/primaryschool/` + id)
      this.firstname.$remove(firstnames, 1)
    }
  },
  mounted() {
    axios
      .get(`https://api-surinsmartcity.herokuapp.com/nongtongsurawittayakom/primaryschool/`)
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


