<template>
  <div>
    <p>จำนวนคนส่ง : {{fetchAPI.length}} คน</p>
    <p>จำนวนคนตอบข้อที่ 1 ถูกต้อง : {{totaltrue1}} คน</p>
    <p>จำนวนคนตอบข้อที่ 2 ถูกต้อง : {{totaltrue2}} คน</p>
    <p>จำนวนคนตอบข้อที่ 3 ถูกต้อง : {{totaltrue3}} คน</p>
    <p>จำนวนคนตอบข้อที่ 4 ถูกต้อง : {{totaltrue4}} คน</p>
    <p>จำนวนคนตอบข้อที่ 5 ถูกต้อง : {{totaltrue5}} คน</p>
    <hr>

    <td>คะแนน</td>
    <td>ชื่อ-นามสกุล</td>
    <td>ห้อง</td>
    <td>เลขที่</td>
    <!-- <td>คะแนน</td> -->
    <tr v-for="total,i in fetchAPI">
<!--       <button class="red" v-on:click="onDelete(total._id,i)">ลบ</button> -->
      <td>{{total.question.question1 + total.question.question2 + total.question.question3 + total.question.question4 + total.question.question5}}</td>
      <td>{{total.titlename}}{{total.firstname}} {{total.lastname}}</td>
      <td>{{total.classroom}}</td>
      <td>{{total.numberinclassroom}}</td>
      <!-- <td>{{total.question.question1}}{{total.question.question2}}{{total.question.question3}}{{total.question.question4}}{{total.question.question5}}</td> -->
    </tr>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      fetchAPI: ""
    };
  },
  mounted() {
    axios
      .get(`https://newapi-ntsurin.herokuapp.com/minigame/`)
      .then(response => {
        this.fetchAPI = response.data;
        //console.log("Data : ", response.data);
      })
      .catch(function(error) {
        //console.log(error);
      });
  },
  methods: {
    onDelete(id, i) {
      axios
        .delete(`https://newapi-ntsurin.herokuapp.com/minigame/` + id, {
          method: "DELETE"
        })
        .then(() => {
          this.fetchAPI.splice(i, 1);
          //this.$delete(this.facebook, index)
        });
    }
  },

computed: {
  totaltrue1: function(){
  var total = [];
  Object.entries(this.fetchAPI).forEach(([key, total1]) => {
      total.push(total1.question.question1) 
  });
  return total.reduce(function(total, num) { 
    return total + num }, 0);
},
  totaltrue2: function(){
  var total = [];
  Object.entries(this.fetchAPI).forEach(([key, total2]) => {
      total.push(total2.question.question2) 
  });
  return total.reduce(function(total, num) { 
    return total + num }, 0);
},
  totaltrue3: function(){
  var total = [];
  Object.entries(this.fetchAPI).forEach(([key, total3]) => {
      total.push(total3.question.question3) 
  });
  return total.reduce(function(total, num) { 
    return total + num }, 0);
},
  totaltrue4: function(){
  var total = [];
  Object.entries(this.fetchAPI).forEach(([key, total4]) => {
      total.push(total4.question.question4) 
  });
  return total.reduce(function(total, num) { 
    return total + num }, 0);
},
  totaltrue5: function(){
  var total = [];
  Object.entries(this.fetchAPI).forEach(([key, total5]) => {
      total.push(total5.question.question5) 
  });
  return total.reduce(function(total, num) { 
    return total + num }, 0);
},
},


};
</script>

<style scoped>
.red {
  background-color: red;
  border-radius: 0.25em;
  border: 1px solid red;
  color: #ffffff;
  padding: 4px 10px;
}
td {
  border: none;
}
</style>
