<template>
  <div>
    <b>หากจังหวัดสุรินทร์กำลังเร่งเดินหน้าพัฒนา เพื่อเข้าสู่ยุค "เมืองอัจฉริยะ (Smart City)" ควรจะพัฒนาด้านใดบ้าง ? (ให้เลือกตอบคนละ 1 ข้อ)</b>
    <p>ยกตัวอย่าง</p>
    <p>1.ด้านการขนส่ง</p>
    <p>2.ด้านการจัดการขยะ</p>
    <p>3.ด้านการเกษตร</p>
    <p>4.ด้านการท่องเที่ยว</p>
    <p>5.ด้านสุขภาพ</p>
    <p>เช่น ควรจะพัฒนาในด้านการท่องเที่ยว เพราะ...</p>
    <hr>

    <form @submit.prevent="onSubmit">
      <p>คำนำหน้านาม</p>
      <select type="text" v-model="titlename" required>
        <option value>- กรุณาเลือกคำนำหน้า -</option>
        <option value="ด.ช.">ด.ช.</option>
        <option value="ด.ญ.">ด.ญ.</option>
        <option value="นาย">นาย</option>
        <option value="นางสาว">นางสาว</option>
      </select>
      <p>ชื่อ (ไม่ต้องใส่ คำนำหน้านาม)</p>
      <input type="text" class="form-control input-md" required v-model="firstname">
      <p>นามสกุล</p>
      <input type="text" class="form-control input-md" required v-model="lastname">
      <p>ห้อง</p>
      <select type="text" v-model="classroom" required>
        <option value>- กรุณาเลือกห้อง -</option>
        <option value="ป.5/1">ป.5/1</option>
        <option value="ป.5/2">ป.5/2</option>
        <option value="ป.5/3">ป.5/3</option>
        <option value="ป.5/4">ป.5/4</option>
        <option value="ป.5/5">ป.5/5</option>
        <option value="ป.5/6">ป.5/6</option>
        <option value="ป.5/7">ป.5/7</option>
        <option value="ป.5/8">ป.5/8</option>
        <option value="ป.5/9">ป.5/9</option>
        <option value="ป.5/10">ป.5/10</option>
      </select>
      <p>เลขที่</p>
      <input
        type="number"
        class="form-control input-md"
        required
        v-model="numberclassroom"
        min="1"
        max="99"
      >
      <p>คำตอบ</p>
      <textarea cols="35" rows="20" v-model="text" required></textarea>
      <br>
      <br>
      <input type="submit" value="ส่งข้อมูล">
    </form>
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
    onSubmit() {
      //console.log(this.firstname, this.lastname);
      axios.post(
        "https://api-surinsmartcity.herokuapp.com/nongtongsurawittayakom/surinsmartcity",
        {
          titlename: this.titlename,
          firstname: this.firstname,
          lastname: this.lastname,
          classroom: this.classroom,
          numberclassroom: this.numberclassroom,
          text: this.text,

          null: (this.titlename = ""),
          null: (this.firstname = ""),
          null: (this.lastname = ""),
          null: (this.classroom = ""),
          null: (this.numberclassroom = ""),
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