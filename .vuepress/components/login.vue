<template>
  <div>
    <h1>สำหรับคุณครู</h1>
    <form @submit.prevent="login">
      <p>
        ชื่อผู้ใช้ &nbsp;&nbsp;
        <input
          type="text"
          class="form-control input-md"
          required
          name="username"
          v-model="input.username"
        >
      </p>
      <p>
        รหัสผ่าน &nbsp;&nbsp;
        <input
          type="password"
          class="form-control input-md"
          required
          name="password"
          v-model="input.password"
        >
      </p>
      <input type="submit" value="เข้าสู่ระบบ">
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      input: {
        username: "",
        password: ""
      }
    };
  },
  methods: {
    login() {
      if (this.input.username == "a") {
        if (this.input.password == "a") {
          location = "backend/";
        } else {
          alert("ชื่อผู้ใช้ หรือ รหัสผ่านไม่ถูกต้อง");
        }
      } else {
        alert("ชื่อผู้ใช้ หรือ รหัสผ่านไม่ถูกต้อง");
      }
    }
  }
};
</script>


<style scoped>
input[type="password"],
input[type="text"],
select,textarea {
  border: 1px solid #e0e0e0;
  padding: 0.85em 0.75em 0.75em 0.75em;
  width: 100%;
  box-sizing: border-box;
  resize: none;
  background: white;
}

input[type="submit"] {
  background-color: #0987ee;
  border-radius: 0.25em;
  border: 1px solid #0987ee;
  color: #ffffff;
  font-size: 1em;
  letter-spacing: 0.025em;
  padding: 0.85em 0.75em 0.75em 0.75em;
  width: 100%;
}
</style>
