<template>
  <div>
    <p>คำตอบ เขียนจดหมายถึงตัวเองในอนาคต</p>
    <p>จำนวนคนส่ง : {{firstname.length}} คน</p>
    <hr>
    <div v-for="firstnames, i in firstname">
      <p>
        ชื่อ : {{firstnames.titlename}} {{firstnames.firstname}} {{firstnames.lastname}}
        <button id="red" v-on:click="onDelete(firstnames._id,i)">Delete</button>
      </p>
      <p>ห้อง : {{firstnames.classroom}} เลขที่ : {{firstnames.numberinclassroom}}</p>
      <p>
        รายละเอียด :
        <button id="gray" v-on:click="editResult = firstnames._id">Edit</button>
        <button id="green" v-on:click="UpdateResult(firstnames)">Update</button>
        <br>
      </p>
      <div v-if="editResult === firstnames._id">คำนำหน้านาม :
        <input type="text" v-model="firstnames.titlename">
        <br>ชื่อ :
        <input type="text" v-model="firstnames.firstname">
        <br>นามสกุล :
        <input type="text" v-model="firstnames.lastname">
        <br>ห้อง :
        <input type="text" v-model="firstnames.classroom">
        <br>เลขที่ :
        <input type="number" v-model="firstnames.numberinclassroom">
      </div>
      <div v-else>
        <textarea rows="15">{{firstnames.text}}</textarea>
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
      firstname: "",
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
          this.firstname.splice(i, 1);
          //this.$delete(this.facebook, index)
        });
    },
    UpdateResult(firstnames) {
      fetch(
        `https://newapi-ntsurin.herokuapp.com/mailfuture/` + firstnames._id,
        {
          body: JSON.stringify(firstnames),
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
        this.firstname = response.data;
        //console.log("Data : ", response.data);
      });
  }
};
</script>


<style scoped>
#red {
  background-color: #ff0000;
  border-radius: 0.25em;
  border: 1px solid #ff0000;
  color: #ffffff;
  font-size: 0.8em;
  padding: 0.5em;
}
#gray {
  background-color: #7e7e7e;
  border-radius: 0.25em;
  border: 1px solid #7e7e7e;
  color: #ffffff;
  font-size: 0.8em;
  padding: 0.5em;
}
#green {
  background-color: #2baf2b;
  border-radius: 0.25em;
  border: 1px solid #2baf2b;
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