<template>
    <div>
       
        <h1>สำหรับคุณครู</h1>
        <form @submit.prevent="login">
        <p>ชื่อผู้ใช้ : &nbsp;&nbsp;
        <input type="text" class="form-control input-md" required="" name="username" v-model="input.username" placeholder="ชื่อผู้ใช้" /></p>
        <p>รหัสผ่าน : &nbsp;&nbsp;
        <input type="password" class="form-control input-md" required="" name="password" v-model="input.password" placeholder="รหัสผ่าน" /></p>
        <input type="submit" value="เข้าสู่ระบบ">
        </form>
    
    </div>
</template>

<script>
    export default {
        data() {
            return {
                input: {
                    username: '',
                    password: ''
                }
            }
        },
        methods: {
            login() {
                if(this.input.username == 'a') {
                    if(this.input.password == 'a') {
                        location="backend/" 
                    } else {
                        alert("ชื่อผู้ใช้ หรือ รหัสผ่านไม่ถูกต้อง");
            
                    }
                } else {
                    alert("ชื่อผู้ใช้ หรือ รหัสผ่านไม่ถูกต้อง");
  
                }
            }
        }
    }
</script>


<style scoped>
form {
  background-color: #ffffff;
  display: block;
  max-width: 90vw;
  margin: 0 auto;
  transition: 250ms box-shadow ease-out, 250ms -webkit-transform ease-out;
  transition: 250ms box-shadow ease-out, 250ms transform ease-out;
  transition: 250ms box-shadow ease-out, 250ms transform ease-out, 250ms -webkit-transform ease-out;
}

input[type="password"],
input[type="text"],
textarea {
  border: 1px solid #e0e0e0;
  padding: 0.85em 0.75em 0.75em 0.75em;
  width: calc(100% - 1.25em);
  transition: 125ms border-color ease-out;
}


input[type="submit"] {
  background-color: #2491eb;
  border-radius: 0.25em;
  border: 1px solid #1277ca;
  color: #ffffff;
  font-size: 1.0em;
  letter-spacing: 0.025em;
  margin-top: 0.25em;
  margin-bottom: 2em;
  padding: 1em;
  transition: 125ms background-color ease-out, 125ms border-color ease-out;
  width: 100%;
}
input[type="submit"]:focus {
  box-shadow: 0 0 0 3px #ffffff, 0 0 0 6px #2491eb;
}

</style>
