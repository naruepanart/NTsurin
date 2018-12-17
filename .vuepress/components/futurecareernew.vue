<template>
  <div>
    <hr>
    <form @submit.prevent="onSubmit">
      <h3>ข้อมูลส่วนตัว</h3>
      <p>คำนำหน้านาม</p>
       <div class="radio-toolbar">
        <input type="radio" id="female" value="ด.ญ." v-model="titlename">
        <label for="female">ด.ญ.</label> &nbsp;
        <input type="radio" id="male" value="ด.ช." v-model="titlename">
        <label for="male">ด.ช.</label>
      </div>
      <!-- <select type="text" v-model="titlename" required>
        <option value>- เลือกคำนำหน้า -</option>
        <option value="ด.ช.">ด.ช.</option>
        <option value="ด.ญ.">ด.ญ.</option>
         <option value="นาย">นาย</option>
        <option value="นางสาว">นางสาว</option>
      </select> -->
      <p>ชื่อ (ไม่ต้องใส่ คำนำหน้านาม)</p>
      <input
        type="text"
        class="form-control input-md"
        required
        v-model="firstname"
        placeholder="ชื่อจริง"
      >
      <p>นามสกุล</p>
      <input
        type="text"
        class="form-control input-md"
        required
        v-model="lastname"
        placeholder="นามสกุล"
      >
      <p>ห้อง</p>
      <select type="text" v-model="classroom" required>
        <option value>- เลือกห้อง -</option>
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
        v-model="numberinclassroom"
        min="1"
        max="99"
        placeholder="เลขที่"
      >
      <h3>คำตอบ</h3>
      <p>อาชีพเดิม จากหัวข้ออาชีพในอนาคต (ครั้งที่ผ่านมา)</p>
      <input
        type="text"
        class="form-control input-md"
        required
        v-model="oldjob"
        placeholder="ตำรวจ"
      >
      <br>
      <p>อาชีพใหม่</p>
      <textarea rows="10" v-model="newjob" required placeholder="นักบินอวกาศ เพราะ..."></textarea>
      <p>เงินเดือนที่ต้องการ / ต่อเดือน (เมื่ออายุครบ 30 ปี)</p>
      <select type="text" v-model="salary" required>
        <option value>- เลือกเงินเดือนที่ต้องการ -</option>
        <option value="10,000">10,000</option>
        <option value="20,000">20,000</option>
        <option value="30,000">30,000</option>
        <option value="40,000">40,000</option>
        <option value="50,000">50,000</option>
        <option value="60,000">60,000</option>
        <option value="70,000">70,000</option>
        <option value="80,000">80,000</option>
        <option value="90,000">90,000</option>
        <option value="100,000">100,000</option>
        <option value="200,000">200,000</option>
        <option value="300,000">300,000</option>
        <option value="400,000">400,000</option>
        <option value="500,000">500,000</option>
        <option value="1,000,000">1,000,000</option>
      </select>

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
      numberinclassroom: "",
      oldjob: "",
      newjob: "",
      salary: ""
    };
  },
  methods: {
    onSubmit() {
      axios.post("https://newapi-ntsurin.herokuapp.com/futurecareernew", {
        titlename: this.titlename,
        firstname: this.firstname,
        lastname: this.lastname,
        classroom: this.classroom,
        numberinclassroom: this.numberinclassroom,
        oldjob: this.oldjob,
        newjob: this.newjob,
        salary: this.salary,

        null: (this.titlename = ""),
        null: (this.firstname = ""),
        null: (this.lastname = ""),
        null: (this.classroom = ""),
        null: (this.numberinclassroom = ""),
        null: (this.oldjob = ""),
        null: (this.newjob = ""),
        null: (this.salary = "")
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
  border-radius: 0.25em;
  border: 1px solid #0987ee;
  color: #ffffff;
  font-size: 1em;
  letter-spacing: 0.025em;
  padding: 0.85em 0.75em 0.75em 0.75em;
  width: 100%;
}

.radio-toolbar input[type="radio"] {
  display: none;
}

.radio-toolbar label {
  display: inline-block;
  background-color: #ffffff;
  border-radius: 0.25em;
  border: 1px solid #0987ee;
  padding: 4px 10px;
  font-size: 15px;
  font-family: Arial;
  color: black;
}

.radio-toolbar label:hover {
  background-color: #e8eef7;
}

.radio-toolbar input[type="radio"]:checked + label {
  background-color: #0987ee;
  border-color: #0987ee;
  color: #ffffff;
}
</style>