<template>
  <div>
    <p>จำนวนคนที่ส่ง : {{fetchAPI.length}} คน - เรียงตามกลุ่ม</p>
    <td>กลุ่มที่</td>
    <td>ชื่อ</td>
    <td>นามสกุล</td>
    <td>เลขที่</td>
    <td>คะแนน</td>
    <tr v-for="total,i in fetchAPI">
      <td>{{total.group}}</td>
      <td>{{total.profiles.titlename}} {{total.profiles.firstname}}</td>
      <td>{{total.profiles.lastname}}</td>
      <td>{{total.profiles.numberinclassroom}}</td>
      <td>{{total.status}}</td>
      <!-- <button v-on:click="onDelete(total._id,i)">ลบ</button> -->
      <hr>
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
      .get(`https://newapi-ntsurin.herokuapp.com/technopreneur/`)
      .then(response => {
        this.fetchAPI = response.data;
        //console.log("Data : ", response.data);
      })
      .catch(function(error) {
        console.log(error);
      });
  },
  methods: {
    onDelete(id, i) {
      axios
        .delete(`https://newapi-ntsurin.herokuapp.com/technopreneur/` + id, {
          method: "DELETE"
        })
        .then(() => {
          this.fetchAPI.splice(i, 1);
          //this.$delete(this.facebook, index)
        });
    }
  }
};
</script>

<style scoped>
td {
  border: none;
}
</style>
