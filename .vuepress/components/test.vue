<template>
  <div>
    <center>
    <form @submit.prevent="onSubmit()">
    <p>ชื่อจริง : &nbsp;&nbsp;
    <input type="text" class="form-control input-md" placeholder="ด.ช.จิรายุ" required="" v-model="firstname" size="20"></p>
    <p>นามสกุล : &nbsp;&nbsp;
    <input type="text" class="form-control input-md" placeholder="บินทะลุบ้าน" required="" v-model="lastname" size="20"></p>
    <p>ชั้นประถมศึกษาปีที่ : &nbsp;&nbsp;
    <input type="text" class="form-control input-md" placeholder="5/1" required="" v-model="classroom" size="10"></p>
    <p>เลขที่ : &nbsp;&nbsp;
    <input type="text" class="form-control input-md" placeholder="1" required="" v-model="numberclassroom" size="10"></p>
    <hr>
    <span style="font-weight:bold;">หากจังหวัดสุรินทร์กำลังเร่งเดินหน้าพัฒนา เพื่อเข้าสู่ยุค "เมืองอัจฉริยะ (Smart City)" ควรจะพัฒนาด้านใดบ้าง ?</span>
    <p>เช่น ควรจะพัฒนาในด้าน การท่องเที่ยว เพราะ...</p>
    <textarea cols="35" rows="20" v-model="text" placeholder="ควรจะพัฒนาในด้าน... เพราะ..." required=""></textarea><br>
    <a href="https://www.google.co.th/search?q=smart+city&rlz=1C1GCEA_enTH819TH819&oq=smart&aqs=chrome.2.69i57j69i61j69i59j69i61j0l2.5351j0j7&sourceid=chrome&ie=UTF-8">แหล่งสืบค้นข้อมูล</a>
    <br>
    <hr>
 <strong>ตรวจสอบข้อมูลก่อนส่ง</strong>
 <p>ชื่อจริง : {{ firstname }}</p>
 <p>นามสกุล : {{ lastname }}</p>
 <p>ชั้นประถมศึกษาปีที่ : {{ classroom }}</p>
 <p>เลขที่ : {{ numberclassroom }}</p>
 <button style="height:40px;width:300px" type="submit">ส่งข้อมูล</button>
   </form>
   </center>

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
    onSubmit() {
      //console.log(this.firstname, this.lastname);
      axios.post("https://api-surinsmartcity.herokuapp.com/nongtongsurawittayakom/primaryschool", {
          firstname: this.firstname,
          lastname: this.lastname,
          classroom: this.classroom,
          numberclassroom: this.numberclassroom,
          text: this.text
        })
        .then(response => {
          this.firstname = ''
          this.lastname = ''
          this.classroom = ''
          this.numberclassroom = ''
          this.text = ''
          location.reload()
          location.href = "https://surinsmartcity.netlify.com/thanksyou/"
        });
    },
   
  },
};
</script>

