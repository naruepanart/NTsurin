<template>
  <div>
    <form @submit.prevent="onSubmit">
      <h3>ข้อมูลส่วนตัว</h3>
      คำนำหน้านาม :
      <label>
        <input type="radio" name="titlename" value="ด.ญ." v-model="titlename" required>ด.ญ.
      </label> &nbsp;
      <label>
        <input type="radio" name="titlename" value="ด.ช." v-model="titlename">ด.ช.
      </label>

      <p>ชื่อจริง (ไม่ต้องใส่ คำนำหน้านาม) :</p>
      <input
        type="text"
        class="form-control"
        required
        v-model="firstname"
        placeholder="ชื่อจริง"
      >
      <p>นามสกุล :</p>
      <input
        type="text"
        class="form-control"
        required
        v-model="lastname"
        placeholder="นามสกุล"
      >
      <p>ห้อง :</p>
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
      <p>เลขที่ :</p>
      <input
        type="number"
        class="form-control"
        required
        v-model="numberinclassroom"
        min="1"
        max="99"
        placeholder="เลขที่"
      >
      <h3>ให้นักเรียนตอบคำถามต่อไปนี้ให้ถูกต้อง</h3>
      <h4>โดย ความหมายในภาพจะสอดคล้องกับคำตอบ</h4>
      <p>ข้อที่ 1 :</p>
      <img src="https://scontent.fbkk5-6.fna.fbcdn.net/v/t1.0-9/374435_130489380471662_623811099_n.jpg?_nc_cat=101&_nc_eui2=AeHi0ad08d8N0q_PjsIcG15fnvOOYSLY0zDkIylpWhmfgY5TjtEKmai28YcuzvFHcz3FCFMFV0kgwtCT1seXK__cER8u1F1PjLf0wyzZu3QtgA&_nc_ht=scontent.fbkk5-6.fna&oh=138eb7d58a937e27ab591dd8650a43d3&oe=5C9068B7">
      <select type="number" v-model="question.question1" required>
        <option value>- เลือกคำตอบข้อที่ 1 -</option>
        <option value="1">อาหารจีน</option>
        <option value="0">อาหารไทย</option>
        <option value="0">สี่หารสอง</option>
        <option value="0">หกหารสาม</option>
        <option value="0">มองทางขวา</option>
      </select>
      <p>ข้อที่ 2 :</p>
      <img src="https://scontent.fbkk5-1.fna.fbcdn.net/v/t1.0-9/563664_130489077138359_1939057639_n.jpg?_nc_cat=109&_nc_eui2=AeFJ9RZWeHAtnIrzpMzfnALSqbJ9Zfacm5vN8D_cWv-vfhwOQVAgTugJepzN8xTDPjzVkd5tl01rO6gOgQv8thIVe-NyWMhRRsyH-riMnHIRRQ&_nc_ht=scontent.fbkk5-1.fna&oh=01f5805fd525e9905f2caee50e89d632&oe=5CA985FA">
      <select type="number" v-model="question.question2" required>
        <option value>- เลือกคำตอบข้อที่ 2 -</option>
        <option value="1">ไม้ขนไก่</option>
        <option value="0">รถขนไก่</option>
        <option value="0">ไม้จับไก่</option>
        <option value="0">ไข้หวัดนก</option>
        <option value="0">ใช้แรงงาน</option>
      </select>
      <p>ข้อที่ 3 :</p>
      <img src="https://scontent.fbkk5-5.fna.fbcdn.net/v/t1.0-9/20919_130489583804975_1476343657_n.jpg?_nc_cat=100&_nc_eui2=AeEid47EwC5siruC0tdd2OM9FEYDU_QLIfDFcD9y9WENcTJ5dWahn_JlwUyBIHcIaS-kTLZFN4kr7CFikRVrGEs4wosY3NZgNbs0x4LlgNvbsw&_nc_ht=scontent.fbkk5-5.fna&oh=eda18b65a6d1470225b521266bc37226&oe=5CA51DC1">
      <select type="number" v-model="question.question3" required>
        <option value>- เลือกคำตอบข้อที่ 3 -</option>
        <option value="1">กลับหัวกลับหาง</option>
        <option value="0">กลับตัวกลับใจ</option>
        <option value="0">ลองผิดลองถูก</option>
        <option value="0">เรือหางยาว</option>
        <option value="0">เรือสำเภา</option>
      </select>
      <p>ข้อที่ 4 :</p>
       <img src="https://scontent.fbkk5-1.fna.fbcdn.net/v/t1.0-9/374403_130489940471606_1997416462_n.jpg?_nc_cat=109&_nc_eui2=AeGR0jUAP263cc41OeQoyc7Rz4P356dnV8qonwi3xEe79RXYTapiNTooWHLMOCyA0k0yKfe1I6buvQjftr085yRAYwWiV5T8TdHH3AF8M246AQ&_nc_ht=scontent.fbkk5-1.fna&oh=cd630469287ee1173b2ab78b50bb397d&oe=5CA6E777">
      <select type="number" v-model="question.question4" required>
        <option value>- เลือกคำตอบข้อที่ 4 -</option>
        <option value="1">เป็ดปักกิ่ง</option>
        <option value="0">เป็ดจับเข็ม</option>
        <option value="0">เป็ดเย็บผ้า</option>
        <option value="0">เปลี่ยนเข็มใหม่</option>
        <option value="0">ดูกิ่งไม้</option>
      </select>
      <p>ข้อที่ 5 :</p>
       <img src="https://scontent.fbkk5-5.fna.fbcdn.net/v/t1.0-9/58873_130489510471649_2068825409_n.jpg?_nc_cat=100&_nc_eui2=AeHnVyd6q2LtANzcf2hfwH9ubCCfjDOkLWOXmrtZlFrLRBN20zTJqmgpyPeKobUP7jOd02Ra-Fd0XoZvC3fPs5PdOeOxNH0-S1h2RMpbWDkKjQ&_nc_ht=scontent.fbkk5-5.fna&oh=7f6e5776e3ad9ab65045a5126a7728d6&oe=5CA506C9">
      <select type="number" v-model="question.question5" required>
        <option value>- เลือกคำตอบข้อที่ 5 -</option>
        <option value="1">ไข่เยี่ยวม้า</option>
        <option value="0">ควายมองไข่</option>
        <option value="0">ไก่นอนหลับ</option>
        <option value="0">ครูชี้ฟ้า</option>
        <option value="0">ขวดต่างสี</option>
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
      question: {
        question1: "",
        question2: "",
        question3: "",
        question4: "",
        question5: ""
      }
    };
  },
  methods: {
    onSubmit() {
      axios.post("https://newapi-ntsurin.herokuapp.com/minigame", {
        titlename: this.titlename,
        firstname: this.firstname,
        lastname: this.lastname,
        classroom: this.classroom,
        numberinclassroom: this.numberinclassroom,
        question: this.question,

        null: (this.titlename = ""),
        null: (this.firstname = ""),
        null: (this.lastname = ""),
        null: (this.classroom = ""),
        null: (this.numberinclassroom = ""),
        null: (this.question = "")

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