<template>
  <div>  
    <p>คำตอบ สมาร์ทซิตี้</p>
    <p>จำนวนคนส่ง : {{firstname.length}} คน</p>
    <hr>
       <div v-for="firstnames, i in firstname">
         <p>ชื่อ : {{firstnames.firstname}} {{firstnames.lastname}}&nbsp;
           <button v-on:click="onDelete(firstnames._id,i)">Delete</button></p>
        <p>ห้อง : {{firstnames.classroom}} เลขที่ : {{firstnames.numberclassroom}}</p>
        <p>รายละเอียด : <br>{{firstnames.text}}</p>
      </div>
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
        `https://api-surinsmartcity.herokuapp.com/nongtongsurawittayakom/surinsmartcity/` + id, {
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


