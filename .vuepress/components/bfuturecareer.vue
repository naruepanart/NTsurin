<template>
    <div>
    <center>
    <b>ในอนาคต คิดว่าตัวเองจะประกอบอาชีพอะไร และ เพราะอะไร ?</b>
    <hr>
    <form @submit.prevent="onSubmit">
    <p>ชื่อจริง : &nbsp;&nbsp;
    <input type="text" class="form-control input-md" placeholder="ด.ช.จิรายุ" required="" v-model="firstname" size="20"></p>
    <p>นามสกุล : &nbsp;&nbsp;
    <input type="text" class="form-control input-md" placeholder="บินทะลุบ้าน" required="" v-model="lastname" size="20"></p>
    <p>ห้อง : &nbsp;&nbsp;
    <input type="text" class="form-control input-md" placeholder="5/1" required="" v-model="classroom" size="10"></p>
    <p>เลขที่ : &nbsp;&nbsp;
    <input type="number" class="form-control input-md" placeholder="1" required="" v-model="numberclassroom" size="10" min="1"></p>
    <hr>
    <textarea cols="35" rows="20" v-model="text" placeholder="ต้องการประกอบอาชีพ... เพราะ..." required=""></textarea><br>
    <br>
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
      axios
        .post(
          "https://api-surinsmartcity.herokuapp.com/nongtongsurawittayakom/futurecareer", {
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
        //this.firstname.push({link: this.link, picture: this.picture})
        alert('ส่งเรียบร้อยแล้ว');
    }
  }
};
</script>

