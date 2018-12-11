<template>
  <div>
    <p>คำตอบ เขียนจดหมายถึงตัวเองในอนาคต</p>
    <p>จำนวนคนส่ง : {{firstname.length}} คน</p>
    <hr>
    <div v-for="firstnames, i in firstname">
      <p>
        ชื่อ : {{firstnames.titlename}}{{firstnames.firstname}} {{firstnames.lastname}}&nbsp;
        <button
          v-on:click="onDelete(firstnames._id,i)"
        >Delete</button>
      </p>
      <p>ห้อง : {{firstnames.classroom}} เลขที่ : {{firstnames.numberinclassroom}}</p>
      <p>รายละเอียด :
        <br>
        <textarea rows="20">{{firstnames.text}}</textarea>
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
      numberinclassroom: "",
      text: ""
    };
  },
  methods: {
    onDelete(id, i) {
      axios
        .delete(
          `https://newapi-ntsurin.herokuapp.com/mailfuture/` +
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
        `https://newapi-ntsurin.herokuapp.com/mailfuture/`
      )
      .then(response => {
        this.firstname = response.data.reverse();
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
textarea {
  border: 1px solid #e0e0e0;
  padding: 0.85em 0.75em 0.75em 0.75em;
  width: calc(100% - 1.25em);
  resize: none;
}
</style>