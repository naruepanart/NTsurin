<template>
  <div>
    <p>จำนวนทีมที่ส่ง : {{fetchAPI.length}} ทีม</p>

    <div v-for="total,i in fetchAPI">
            <tr>
        <td colspan="2">{{total.group}}</td>
         <td>ห้อง {{total.classroom}}</td>
        <!-- <button v-on:click="onDelete(total._id,i)">ลบ</button> -->
      </tr>
      
      <tr>
        <td>{{total.profiles.titlename1}} {{total.profiles.firstname1}}</td>
        <td>{{total.profiles.lastname1}}</td>
        <td>เลขที่ {{total.profiles.numberinclassroom1}}</td>
        <td>ประธาน</td>
      </tr>

      <tr>
        <td>{{total.profiles.titlename2}} {{total.profiles.firstname2}}</td>
        <td>{{total.profiles.lastname2}}</td>
        <td>เลขที่ {{total.profiles.numberinclassroom2}}</td>
        <td>รองประธาน</td>
      </tr>

      <tr>
        <td>{{total.profiles.titlename3}} {{total.profiles.firstname3}}</td>
        <td>{{total.profiles.lastname3}}</td>
        <td>เลขที่ {{total.profiles.numberinclassroom3}}</td>
        <td>กรรมการ1</td>
      </tr>

      <tr>
        <td>{{total.profiles.titlename4}} {{total.profiles.firstname4}}</td>
        <td>{{total.profiles.lastname4}}</td>
        <td>เลขที่ {{total.profiles.numberinclassroom4}}</td>
        <td>กรรมการ2</td>
      </tr>

      <tr>
        <td>{{total.profiles.titlename5}} {{total.profiles.firstname5}}</td>
        <td>{{total.profiles.lastname5}}</td>
        <td>เลขที่ {{total.profiles.numberinclassroom5}}</td>
        <td>กรรมการ3</td>
      </tr>

      <tr>
        <td>{{total.profiles.titlename6}} {{total.profiles.firstname6}}</td>
        <td>{{total.profiles.lastname6}}</td>
        <td>เลขที่ {{total.profiles.numberinclassroom6}}</td>
        <td>กรรมการ4</td>
      </tr>
      <hr>
    </div>
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
      .get(`https://newapi-ntsurin.herokuapp.com/regtechnopreneur/`)
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
        .delete(`https://newapi-ntsurin.herokuapp.com/regtechnopreneur/` + id, {
          method: "DELETE"
        })
        .then(() => {
          this.fetchAPI.splice(i, 1);
          //this.$delete(this.facebook, index)
        });
    }
  },
};
</script>

<style scoped>
td {
  border: none;
}
</style>
