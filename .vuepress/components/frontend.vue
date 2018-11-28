<template>
    <div>
    <center>
    <form @submit.prevent="onSubmit">
    <p>ชื่อจริง : &nbsp;&nbsp;
    <input type="text" class="form-control input-md" placeholder="ด.ช.จิรายุ" required="" v-model="firstname" size="20"></p>
    <p>นามสกุล : &nbsp;&nbsp;
    <input type="text" class="form-control input-md" placeholder="บินทะลุบ้าน" required="" v-model="lastname" size="20"></p>
    <p>ชั้นประถมศึกษาปีที่ : &nbsp;&nbsp;
    <input type="text" class="form-control input-md" placeholder="5/1" required="" v-model="classroom" size="10"></p>
    <p>เลขที่ : &nbsp;&nbsp;
    <input type="number" class="form-control input-md" placeholder="1" required="" v-model="numberclassroom" size="10" min="1"></p>
    <hr>
    <p>หากจังหวัดสุรินทร์กำลังเร่งเดินหน้าพัฒนา เพื่อเข้าสู่ยุค "เมืองอัจฉริยะ (Smart City)" ควรจะพัฒนาด้านใดบ้าง ? <br> <b>(ให้เลือกตอบคนละ 1 ข้อ)</b></p>
    <p>ยกตัวอย่าง</p>
    <p>1.ด้านการขนส่ง</p>
    <p>2.ด้านการจัดการขยะ</p>
    <p>3.ด้านการเกษตร</p>
    <p>4.ด้านการท่องเที่ยว</p>
    <p>5.ด้านสุขภาพ</p>
    <p>เช่น ควรจะพัฒนาในด้านการท่องเที่ยว เพราะ...</p>
    <textarea cols="35" rows="20" v-model="text" placeholder="ควรจะพัฒนาในด้าน... เพราะ..." required=""></textarea><br>
    <a href="https://www.google.co.th/search?q=smart+city&rlz=1C1GCEA_enTH819TH819&oq=smart&aqs=chrome.2.69i57j69i61j69i59j69i61j0l2.5351j0j7&sourceid=chrome&ie=UTF-8">แหล่งค้นหาคำตอบ</a>
    <br><br>
    <button style="height:40px;width:300px" type="submit">ส่งข้อมูล</button>
    <br><br>
    <a href="/backend/count.html">ตรวจรายชื่อตนเองหลังจากส่งข้อมูลได้ที่นี่</a>
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
      axios
        .post(
          "https://api-surinsmartcity.herokuapp.com/nongtongsurawittayakom/primaryschool", {
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

