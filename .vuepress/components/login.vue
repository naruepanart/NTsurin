<template>
    <div id="login">
          <h1>สำหรับคุณครู</h1>
        <form @submit.prevent="login">
        <p>ชื่อผู้ใช้ : &nbsp;&nbsp;
        <input type="text" class="form-control input-md" required="" name="username" v-model="input.username" placeholder="ชื่อผู้ใช้" /></p>
        <p>รหัสผ่าน : &nbsp;&nbsp;
        <input type="password" class="form-control input-md" required="" name="password" v-model="input.password" placeholder="รหัสผ่าน" /></p>
        <button style="height:40px;width:300px" type="submit">เข้าสู่ระบบ</button>
        </form>
    </div>
</template>

<script>
    export default {
        name: 'Login',
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

