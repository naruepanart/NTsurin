<template>
  <div>
    <b>หากจังหวัดสุรินทร์กำลังเร่งเดินหน้าพัฒนา เพื่อเข้าสู่ยุค "เมืองอัจฉริยะ (Smart City)" ควรจะพัฒนาด้านใดบ้าง ? (ให้เลือกตอบคนละ 1 ข้อ)</b>
    <hr>
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
    onSubmit() {
      //console.log(this.firstname, this.lastname);
      axios.post(
        "https://newapi-ntsurin.herokuapp.com/surinsmartcity",
        {
          titlename: this.titlename,
          firstname: this.firstname,
          lastname: this.lastname,
          classroom: this.classroom,
          numberinclassroom: this.numberinclassroom,
          text: this.text,

          null: (this.titlename = ""),
          null: (this.firstname = ""),
          null: (this.lastname = ""),
          null: (this.classroom = ""),
          null: (this.numberinclassroom = ""),
          null: (this.text = "")
        }
      );
      alert("ส่งข้อมูลเรียบร้อยแล้ว");
    }
  }
};
</script>


<style scoped>
form {
  background-color: #ffffff;
  display: block;
  max-width: 90vw;
  margin: 0 auto;
  transition: 250ms box-shadow ease-out, 250ms -webkit-transform ease-out;
  transition: 250ms box-shadow ease-out, 250ms transform ease-out;
  transition: 250ms box-shadow ease-out, 250ms transform ease-out,
    250ms -webkit-transform ease-out;
}
select[type="text"],
input[type="number"],
input[type="text"],
textarea {
  border: 1px solid #e0e0e0;
  padding: 0.85em 0.75em 0.75em 0.75em;
  width: calc(100% - 1.25em);
}

input[type="submit"] {
  background-color: #0987ee;
  border-radius: 0.25em;
  border: 1px solid #0987ee;
  color: #ffffff;
  font-size: 1em;
  letter-spacing: 0.025em;
  margin-top: 0.25em;
  margin-bottom: 2em;
  padding: 1em;
  width: 100%;
}

select {
  background: white;
}
</style>