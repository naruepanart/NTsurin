<template>
  <div>
    <p>จำนวนคนที่รอตรวจ : {{fetchAPI.length}} คน</p>
    <div v-for="total,i in fetchAPI">
      <b>
        กลุ่มที่ {{total.group}} {{total.namebusiness}}
        <br>
      </b>
      <p>
        {{total.profiles.titlename}} {{total.profiles.firstname}}
        {{total.profiles.lastname}}
        เลขที่ {{total.profiles.numberinclassroom}} &nbsp;
        <!--  <button class="red" v-on:click="onDelete(total._id,i)">ลบ</button>   -->
      </p>

      <tr>
        <td>คะแนน : {{total.status}}</td>
        <td v-if="editResult === total._id">
          <select type="text" v-model="total.status">
            <option value="ไม่ผ่าน">ไม่ผ่าน</option>
            <option value="6">6</option>
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
          </select>
        </td>
        <td>
          <!-- <button class="red" v-on:click="onDelete(total._id,i)">ลบ</button> &nbsp; -->
          <button class="green" v-on:click="editResult = total._id">แก้ไข</button> &nbsp;
          <button class="blue" v-on:click="UpdateResult(total)">อัพเดท</button>
        </td>
      </tr>
      <p>หัวข้อ : {{total.topic}}</p>
      <textarea rows="6">{{total.text}}</textarea>
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
      editResult: null,
      status: ""
    };
  },
  mounted() {
    axios
      .get(`https://newapi-ntsurin.herokuapp.com/technopreneur/getallwaitscore`)
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
        .delete(`https://newapi-ntsurin.herokuapp.com/technopreneur/` + id, {
          method: "DELETE"
        })
        .then(() => {
          this.fetchAPI.splice(i, 1);
          //this.$delete(this.facebook, index)
        });
    },
    UpdateResult(total) {
      fetch(`https://newapi-ntsurin.herokuapp.com/technopreneur/` + total._id, {
        body: JSON.stringify(total),
        method: "PUT",
        headers: {
          "Content-Type": "application/json"
        }
      }).then(() => {
        this.editResult = null;
        //this.$delete(this.facebook, index)
      });
    }
  }
};
</script>

<style scoped>
.red {
  background-color: red;
  border-radius: 0.25em;
  border: 1px solid red;
  color: #ffffff;
  padding: 4px 8px;
}
.green {
  background-color: #34bf49;
  border-radius: 0.25em;
  border: 1px solid #34bf49;
  color: #ffffff;
  padding: 4px 8px;
}

.blue {
  background-color: #0987ee;
  border-radius: 0.25em;
  border: 1px solid #0987ee;
  color: #ffffff;
  padding: 4px 8px;
}
td {
  border: none;
  background-color: white;
}
textarea {
  border: 2px solid #e0e0e0;
  padding: 0.85em 0.75em 0.75em 0.75em;
  width: 100%;
  box-sizing: border-box;
  resize: none;
}
</style>
