<template>
  <div>
    <p>คำตอบ สมาร์ทซิตี้</p>
    <p>จำนวนคนส่ง : {{firstname.length}} คน</p>
    <hr>
    <div v-for="firstnames, i in firstname">
      <p>
        ชื่อ : {{firstnames.titlename}}{{firstnames.firstname}} {{firstnames.lastname}}&nbsp;
        <button
          v-on:click="onDelete(firstnames._id,i)"
        >Delete</button>
      </p>
      <p>ห้อง : {{firstnames.classroom}} เลขที่ : {{firstnames.numberclassroom}}</p>
      <p>รายละเอียด :
        <br>
        {{firstnames.text}}
      </p>
      <hr>
    </div>
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
  methods: {
    onDelete(id, i) {
      axios
        .delete(
          `https://newapi-ntsurin.herokuapp.com/surinsmartcity/` +
            id,
          {
            method: "DELETE"
          }
        )
        .then(() => {
          this.firstname.splice(i, 1);
          //this.$delete(this.facebook, index)
        });
    }
  },
  mounted() {
    axios
      .get(
        `https://newapi-ntsurin.herokuapp.com/surinsmartcity/`
      )
      .then(response => {
        this.firstname = response.data;
        //console.log("Data : ", response.data);
      });
  }
};
</script>



<style scoped>
button {
  background-color: red;
  border-radius: 0.25em;
  border: 1px solid red;
  color: #ffffff;
  font-size: 0.7em;
  padding: 0.5em;
}
</style>