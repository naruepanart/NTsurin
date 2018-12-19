<template>
  <div>
    <p>จำนวนคนส่ง : {{fetchAPI.length}} คน</p>
    <p>จำนวนคนตอบข้อที่ 1 ถูกต้อง : {{totaltrue1}} คน</p>
    <p>จำนวนคนตอบข้อที่ 2 ถูกต้อง : {{totaltrue2}} คน</p>
    <p>จำนวนคนตอบข้อที่ 3 ถูกต้อง : {{totaltrue3}} คน</p>
    <p>จำนวนคนตอบข้อที่ 4 ถูกต้อง : {{totaltrue4}} คน</p>
    <p>จำนวนคนตอบข้อที่ 5 ถูกต้อง : {{totaltrue5}} คน</p>
    <hr>
    <td>ชื่อ</td>
    <td>นามสกุล</td>
    <td>ห้อง</td>
    <td>เลขที่</td>
    <td>คะแนน</td>
    <td>คะแนนรวม</td>
    <tr v-for="total,i in fetchAPI">
      <td>{{total.titlename}}{{total.firstname}}</td>
      <td>{{total.lastname}}</td>
      <td>{{total.classroom}}</td>
      <td>{{total.numberinclassroom}}</td>
      <td>{{total.question.question1}}{{total.question.question2}}{{total.question.question3}}{{total.question.question4}}{{total.question.question5}}</td>
    <td>{{total.question.question1 + total.question.question2 + total.question.question3 + total.question.question4 + total.question.question5}}</td>
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
        console.log(error);
      });
  },
computed: {
  totaltrue1() {
    return this.fetchAPI.reduce(function (sum, total) {
      return sum + total.question.question1 
    }, 0)
  },
  totaltrue2() {
    return this.fetchAPI.reduce(function (sum, total) {
      return sum + total.question.question2 
    }, 0)
  },
  totaltrue3() {
    return this.fetchAPI.reduce(function (sum, total) {
      return sum + total.question.question3 
    }, 0)
  },
  totaltrue4() {
    return this.fetchAPI.reduce(function (sum, total) {
      return sum + total.question.question4 
    }, 0)
  },
  totaltrue5() {
    return this.fetchAPI.reduce(function (sum, total) {
      return sum + total.question.question5 
    }, 0)
  }
}

  // Fetches fetchAPI when the component is created.
  /*  mounted() {
    fetch(`https://apiwarpth-zcrbcgqtob.now.sh/fetchAPI`)
      .then(response => response.json())
      .then(fetchAPI => {
        this.fetchAPI = fetchAPI;
        // console.log(fetchAPI);
      });
  } */
};
</script>

<style scoped>
td {
  border: none;
}
</style>
