<template>
  <div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      group: "",
      classroom: "",
      profiles: {
        titlename: "",
        firstname: "",
        lastname: "",
        numberinclassroom: ""
      }
    };
  },
  methods: {
    onSubmit() {
      axios.post("https://newapi-ntsurin.herokuapp.com/regtechnopreneur", {
        group: this.group,
        classroom: this.classroom,
        profiles: this.profiles,
        titlename: this.titlename,
        firstname: this.firstname,
        lastname: this.lastname,
        numberinclassroom: this.numberinclassroom,

        null: (this.group = ""),
        null: (this.classroom = ""),
        null: (this.profiles = ""),
        null: (this.titlename = ""),
        null: (this.firstname = ""),
        null: (this.lastname = ""),
        null: (this.numberinclassroom = "")
      });
      alert("ส่งข้อมูลเรียบร้อยแล้ว");
    }
  }
};
</script>

<style scoped>
input[type="number"],
input[type="text"],
select,
textarea {
  border: 1px solid #e0e0e0;
  padding: 0.85em 0.75em 0.75em 0.75em;
  width: 100%;
  box-sizing: border-box;
  resize: none;
  background: white;
}

input[type="submit"] {
  background-color: #0987ee;
  border: 1px solid #0987ee;
  color: #ffffff;
  font-size: 1em;
  letter-spacing: 0.025em;
  padding: 0.85em 0.75em 0.75em 0.75em;
  width: 100%;
}
input[type="radio"] {
  height: 12px;
  width: 25px;
  transform: scale(1.2);
}
</style>