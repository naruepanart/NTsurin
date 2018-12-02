<template>
    <div>

    <b>ในอนาคต คิดว่าตัวเองจะประกอบอาชีพอะไร และ เพราะอะไร ?</b>
    <hr>
   
   <form @submit.prevent="onSubmit">
     <p>คำนำหน้านาม</p>
    <select type="text" v-model="titlename" required="">
        <option value="ด.ช.">ด.ช.</option>
        <option value="ด.ญ.">ด.ญ.</option>
        <option value="นาย">นาย</option>
        <option value="นางสาว">นางสาว</option>
    </select>
    <p>ชื่อ</p>
    <input type="text" class="form-control input-md" required="" v-model="firstname">
    <p>นามสกุล </p>
    <input type="text" class="form-control input-md" required="" v-model="lastname">
    <p>ห้อง</p>
     <select type="text" v-model="classroom" required="">
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
    <p>เลขที่ </p>
    <input type="number" class="form-control input-md" required="" v-model="numberclassroom" min="1">
    <p>คำตอบ </p>
    <textarea cols="35" rows="20" v-model="text" required=""></textarea><br>
    <br>
    <input type="submit" value="Post">
    </form>
   
    </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      titlename: '',
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
            titlename: this.titlename,
            firstname: this.firstname,
            lastname: this.lastname,
            classroom: this.classroom,
            numberclassroom: this.numberclassroom,
            text: this.text,
            
            null: this.titlename = '',
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

select[type="text"],
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