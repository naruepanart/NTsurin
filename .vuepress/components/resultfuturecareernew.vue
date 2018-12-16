<template>
  <div>
    <p>คำตอบ อาชีพใหม่ในอนาคต</p>
    <p>จำนวนคนส่ง : {{fetchAPI.length}} คน</p>
    <hr>
    <div v-for="total, i in fetchAPI">
      <p>{{total.titlename}} {{total.firstname}} {{total.lastname}}
      {{total.classroom}} เลขที่ {{total.numberinclassroom}}
      </p>
      <p>
        <button class="red" v-on:click="onDelete(total._id,i)">ลบ</button>&nbsp;
        <button class="green" v-on:click="editResult = total._id">แก้ไข</button>&nbsp;
        <button class="blue" v-on:click="UpdateResult(total)">อัพเดท</button>
        <br>
      </p>
      <div v-if="editResult === total._id">คำนำหน้านาม 
        <input type="text" v-model="total.titlename">
        <br>ชื่อ 
        <input type="text" v-model="total.firstname">
        <br>นามสกุล 
        <input type="text" v-model="total.lastname">
        <br>ห้อง 
        <input type="text" v-model="total.classroom">
        <br>เลขที่ 
        <input type="number" v-model="total.numberinclassroom">
      </div>
      <div v-else>
        <p>อาชีพเดิม : {{total.oldjob}}</p>
        <p>อาชีพใหม่ : {{total.newjob}}</p>
        <p>เงินเดือนที่ต้องการ / ต่อเดือน : {{total.salary}}</p>
      </div>
      <hr>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      fetchAPI: "",
      editResult: null
    };
  },
  methods: {
    onDelete(id, i) {
      axios
        .delete(`https://newapi-ntsurin.herokuapp.com/futurecareernew/` + id, {
          method: "DELETE"
        })
        .then(() => {
          this.fetchAPI.splice(i, 1);
          //this.$delete(this.facebook, index)
        });
    },
    UpdateResult(total) {
      fetch(
        `https://newapi-ntsurin.herokuapp.com/futurecareernew/` + total._id,
        {
          body: JSON.stringify(total),
          method: "PUT",
          headers: {
            "Content-Type": "application/json"
          }
        }
      ).then(() => {
        this.editResult = null;
        //this.$delete(this.facebook, index)
      });
    }
  },
  mounted() {
    axios
      .get(`https://newapi-ntsurin.herokuapp.com/futurecareernew/`)
      .then(response => {
        this.fetchAPI = response.data;
        //console.log("Data : ", response.data);
      })
      .catch(err => {
        console.log(err)
      })
  }
};
</script>


<style scoped>
td {
  border: none;
}
.red {
  background-color: red;
  border-radius: 0.25em;
  border: 1px solid red;
  color: #ffffff;
  padding: 4px 10px;
}

.green {
  background-color: #34bf49;
  border-radius: 0.25em;
  border: 1px solid #34bf49;
  color: #ffffff;
  padding: 4px 10px;
}

.blue {
  background-color: #0987ee;
  border-radius: 0.25em;
  border: 1px solid #0987ee;
  color: #ffffff;
  padding: 4px 10px;
}

input[type="number"],
input[type="text"],
textarea {
  border: 2px solid #e0e0e0;
  padding: 0.85em 0.75em 0.75em 0.75em;
  width: calc(100% - 1.25em);
  resize: none;
}
</style>

