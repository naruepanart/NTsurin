<template>
  <div>
    <p>คำตอบ เขียนจดหมายถึงตัวเองในอนาคต</p>
    <p>จำนวนคนส่ง : {{fetchAPI.length}} คน</p>
    <hr>
    <div v-for="total, i in fetchAPI">
      <p>{{total.titlename}} {{total.firstname}} {{total.lastname}}
        &nbsp;
      {{total.classroom}} เลขที่ {{total.numberinclassroom}}
      </p>
      <p>
        <button class="red" v-on:click="onDelete(total._id,i)">ลบ</button>
        <button class="gray" v-on:click="editResult = total._id">แก้ไข</button>
        <button class="green" v-on:click="UpdateResult(total)">อัพเดท</button>
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
        <textarea rows="15">{{total.text}}</textarea>
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
        .delete(`https://newapi-ntsurin.herokuapp.com/mailfuture/` + id, {
          method: "DELETE"
        })
        .then(() => {
          this.fetchAPI.splice(i, 1);
          //this.$delete(this.facebook, index)
        });
    },
    UpdateResult(total) {
      fetch(
        `https://newapi-ntsurin.herokuapp.com/mailfuture/` + total._id,
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
      .get(`https://newapi-ntsurin.herokuapp.com/mailfuture/`)
      .then(response => {
        this.fetchAPI = response.data;
        //console.log("Data : ", response.data);
      });
  }
};
</script>


<style scoped>
td {
  border: none;
}
.red {
  background-color: white;
  border-radius: 0.25em;
  border: none;
  padding: 7px 28px;
}
.red:hover {
  background-color: red;
  color: white;
}

.gray {
  background-color: white;
  border-radius: 0.25em;
  border: none;
  padding: 7px 28px;
}
.gray:hover {
  background-color: #ff9900;
  color: white;
}
.green {
  background-color: white;
  border-radius: 0.25em;
  border: none;
  padding: 7px 28px;
}
.green:hover {
  background-color: #00ad45;
  color: white;
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

