<template>
  <div>
    <p>คำตอบ เขียนจดหมายถึงตัวเองในอนาคต</p>
    <p>จำนวนคนส่ง : {{fetchAPI.length}} คน</p>
    <hr>
    <div v-for="total, i in fetchAPI">
      <p>{{total.titlename}} {{total.firstname}} {{total.lastname}} -
      {{total.classroom}} เลขที่ {{total.numberinclassroom}}
      </p>
      <p>
        รายละเอียด :
        <button class="red" v-on:click="onDelete(total._id,i)">Delete</button>
        -
        <button class="gray" v-on:click="editResult = total._id">Edit</button>&nbsp;
        <button class="green" v-on:click="UpdateResult(total)">Update</button>
        <br>
      </p>
      <div v-if="editResult === total._id">คำนำหน้านาม :
        <input type="text" v-model="total.titlename">
        <br>ชื่อ :
        <input type="text" v-model="total.firstname">
        <br>นามสกุล :
        <input type="text" v-model="total.lastname">
        <br>ห้อง :
        <input type="text" v-model="total.classroom">
        <br>เลขที่ :
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
  background-color: #ff0000;
  border-radius: 0.25em;
  border: 1px solid #ff0000;
  color: #ffffff;
  font-size: 0.8em;
  padding: 0.5em;
}
.gray {
  background-color: #585a5c;
  border-radius: 0.25em;
  border: 1px solid #585a5c;
  color: #ffffff;
  font-size: 0.8em;
  padding: 0.5em;
  
}
.green {
  background-color: #05cc47;
  border-radius: 0.25em;
  border: 1px solid #05cc47;
  color: #ffffff;
  font-size: 0.8em;
  padding: 0.5em;
}

input[type="number"],
input[type="text"],
textarea {
  border: 1px solid #e0e0e0;
  padding: 0.85em 0.75em 0.75em 0.75em;
  width: calc(100% - 1.25em);
  resize: none;
}
</style>