<template>
  <div>
    <p>คำตอบ สมาร์ทซิตี้</p>
    <p>จำนวนคนส่ง : {{fetchAPI.length}} คน</p>
    <hr>
    <div v-for="total, i in fetchAPI">
      <p>
        ชื่อ : {{total.titlename}}{{total.firstname}} {{total.lastname}}&nbsp;
        <button
          v-on:click="onDelete(total._id,i)"
        >Delete</button>
      </p>
      <p>ห้อง : {{total.classroom}} เลขที่ : {{total.numberclassroom}}</p>
      <p>รายละเอียด :
        <br>
        {{total.text}}
      </p>
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
  methods: {
    onDelete(id, i) {
      axios
        .delete(
          `https://newapi-ntsurin.herokuapp.com/surinsmartcity/` +
            id,
          {
            method: "DELETE"
          }
        )
        .then(() => {
          this.fetchAPI.splice(i, 1);
          //this.$delete(this.facebook, index)
        });
    }
  },
  mounted() {
    axios
      .get(
        `https://newapi-ntsurin.herokuapp.com/surinsmartcity/`
      )
      .then(response => {
        this.fetchAPI = response.data;
        //console.log("Data : ", response.data);
      });
  }
};
</script>



<style scoped>
button {
  background-color: red;
  border-radius: 0.25em;
  border: 1px solid red;
  color: #ffffff;
  font-size: 0.7em;
  padding: 0.5em;
}
</style>