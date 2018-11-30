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
    <p>ชื่อจริง</p>
    <input type="text" class="form-control input-md" placeholder="ด.ช.จิรายุ" required="" v-model="firstname" size="20">
  
    <p>นามสกุล </p>
    <input type="text" class="form-control input-md" placeholder="บินทะลุบ้าน" required="" v-model="lastname" size="20">
    <p>ห้อง </p>
    <input type="text" class="form-control input-md" placeholder="5/1" required="" v-model="classroom" size="10">
    <p>เลขที่ </p>
    <input type="number" class="form-control input-md" placeholder="1" required="" v-model="numberclassroom" size="10" min="1">
    <p>คำตอบ </p>
    <textarea cols="35" rows="20" v-model="text" placeholder="ควรจะพัฒนาในด้าน... เพราะ..." required=""></textarea><br>
    <br>
    <input type="submit" value="Post">
    </form>
    
    </div>
</template>

<script>
import axios from 'axios';

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
    onSubmit() {
      //console.log(this.firstname, this.lastname);
      axios
        .post(
          "https://api-surinsmartcity.herokuapp.com/nongtongsurawittayakom/surinsmartcity", {
            firstname: this.firstname,
            lastname: this.lastname,
            classroom: this.classroom,
            numberclassroom: this.numberclassroom,
            text: this.text,
            
            null: this.firstname = '',
            null: this.lastname = '',
            null: this.classroom = '',
            null: this.numberclassroom = '',
            null: this.text = '',
        })
        alert('ส่งเรียบร้อยแล้ว');
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
  transition: 250ms box-shadow ease-out, 250ms transform ease-out, 250ms -webkit-transform ease-out;
}

input[type="number"],
input[type="text"],
textarea {
  -webkit-appearance: none;
     -moz-appearance: none;
          appearance: none;
  border: 1px solid #e0e0e0;
  padding: 0.85em 0.75em 0.75em 0.75em;
  width: calc(100% - 1.25em);
  transition: 125ms border-color ease-out;
}


input[type="submit"] {
  background-color: #2491eb;
  border-radius: 0.25em;
  border: 1px solid #1277ca;
  color: #ffffff;
  font-size: 1.0em;
  letter-spacing: 0.025em;
  margin-top: 0.25em;
  margin-bottom: 2em;
  padding: 1em;
  transition: 125ms background-color ease-out, 125ms border-color ease-out;
  width: 100%;
}
input[type="submit"]:focus {
  box-shadow: 0 0 0 3px #ffffff, 0 0 0 6px #2491eb;
}

</style>