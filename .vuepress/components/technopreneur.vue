<template>
  <div>
    <form @submit.prevent="onSubmit">
      <b>เลขกลุ่มกับเลขธุรกิจ ต้องตรงกัน 
        <a href="https://www.picz.in.th/image/91aPMa">ดูตัวอย่างได้ที่นี่</a>
      </b>
      
      <p>กลุ่ม :</p>
      <select type="number" v-model="group" required>
        <option value>- เลือกกลุ่ม -</option>
        <option value="1">1</option>
        <option value="2">2</option>
        <option value="3">3</option>
        <option value="4">4</option>
        <option value="5">5</option>
        <option value="6">6</option>
        <option value="7">7</option>
        <option value="8">8</option>
        <option value="9">9</option>
        <option value="10">10</option>
        <option value="11">11</option>
        <option value="12">12</option>
        <option value="13">13</option>
        <option value="14">14</option>
        <option value="15">15</option>
        <option value="16">16</option>
        <option value="17">17</option>
        <option value="18">18</option>
        <option value="19">19</option>
        <option value="20">20</option>
        <option value="21">21</option>
        <option value="22">22</option>
        <option value="23">23</option>
        <option value="24">24</option>
        <option value="25">25</option>
        <option value="26">26</option>
        <option value="27">27</option>
        <option value="28">28</option>
        <option value="29">29</option>
        <option value="30">30</option>
        <option value="31">31</option>
        <option value="32">32</option>
        <option value="33">33</option>
        <option value="34">34</option>
        <option value="35">35</option>
        <option value="36">36</option>
        <option value="37">37</option>
        <option value="38">38</option>
        <option value="39">39</option>
        <option value="40">40</option>
        <option value="41">41</option>
        <option value="42">42</option>
        <option value="43">43</option>
        <option value="44">44</option>
        <option value="45">45</option>
        <option value="46">46</option>
        <option value="47">47</option>
        <option value="48">48</option>
        <option value="49">49</option>
        <option value="50">50</option>
      </select>

      <p>ธุรกิจ :</p>
      <select type="text" v-model="namebusiness" required>
        <option value>- เลือกธุรกิจ -</option>
        <option value="ธุรกิจส่งออกมันสําปะหลัง">1.ธุรกิจส่งออกมันสําปะหลัง</option>
        <option value="ธุรกิจน้ำดื่ม">2.ธุรกิจน้ำดื่ม</option>
        <option value="ธุรกิจขายไอศครีม">3.ธุรกิจขายไอศครีม</option>
        <option value="ธุรกิจร้านอาหารไทย">4.ธุรกิจร้านอาหารไทย</option>
        <option value="ธุรกิจรถตู้รับส่งนักเรียน">5.ธุรกิจรถตู้รับส่งนักเรียน</option>
        <option value="ธุรกิจร้านขายตุ๊กตา">6.ธุรกิจร้านขายตุ๊กตา</option>
        <option value="ธุรกิจร้านถ่ายรูป">7.ธุรกิจร้านถ่ายรูป</option>
        <option value="ธุรกิจร้านก๋วยเตี๋ยว">8.ธุรกิจร้านก๋วยเตี๋ยว</option>
        <option value="ธุรกิจร้านขนมเบอเกอรี่">9.ธุรกิจร้านขนมเบอเกอรี่</option>
        <option value="ธุรกิจร้านกาแฟ">10.ธุรกิจร้านกาแฟ</option>
        <option value="ธุรกิจขายบ้าน">11.ธุรกิจขายบ้าน</option>
        <option value="ธุรกิจจำหน่ายจักรยานยนต์">12.ธุรกิจจำหน่ายจักรยานยนต์</option>
        <option value="ธุรกิจร้านอินเตอร์เน็ต">13.ธุรกิจร้านอินเตอร์เน็ต</option>
        <option value="ธุรกิจอาหารเสริม">14.ธุรกิจอาหารเสริม</option>
        <option value="ธุรกิจเครื่องเขียน">15.ธุรกิจเครื่องเขียน</option>
        <option value="ธุรกิจติวเตอร์">16.ธุรกิจติวเตอร์</option>
        <option value="ธุรกิจบริการรับส่งของในประเทศ">17.ธุรกิจบริการรับส่งของในประเทศ</option>
        <option value="ธุรกิจร้านอาหารจีน">18.ธุรกิจร้านอาหารจีน</option>
        <option value="ธุรกิจร้านตัดขนสุนัข">19.ธุรกิจร้านตัดขนสุนัข</option>
        <option value="ธุรกิจร้านอาหารญี่ปุ่น">20.ธุรกิจร้านอาหารญี่ปุ่น</option>
        <option value="ธุรกิจหอพัก">21.ธุรกิจหอพัก</option>
        <option value="ธุรกิจนำเข้าสินค้า">22.ธุรกิจนำเข้าสินค้า</option>
        <option value="ธุรกิจส่งออกสินค้า">23.ธุรกิจส่งออกสินค้า</option>
        <option value="ธุรกิจซ่อมบ้าน">24.ธุรกิจซ่อมบ้าน</option>
        <option value="ธุรกิจร้านขายเสื้อผ้าผู้หญิง">25.ธุรกิจร้านขายเสื้อผ้าผู้หญิง</option>
        <option value="ธุรกิจร้านขายต้นไม้">26.ธุรกิจร้านขายต้นไม้</option>
        <option value="ธุรกิจร้านอาหารญี่ปุ่น">27.ธุรกิจร้านอาหารญี่ปุ่น</option>
        <option value="ธุรกิจร้านเนื้อย่าง">28.ธุรกิจร้านเนื้อย่าง</option>
        <option value="ธุรกิจร้านขายยางรถยนต์">29.ธุรกิจร้านขายยางรถยนต์</option>
        <option value="ธุรกิจร้านขายเสื้อผ้าผู้ชาย">30.ธุรกิจร้านขายเสื้อผ้าผู้ชาย</option>
        <option value="ธุรกิจแปรรูปอาหาร">31.ธุรกิจแปรรูปอาหาร</option>
        <option value="ธุรกิจให้บริการอินเตอร์เน็ต">32.ธุรกิจให้บริการอินเตอร์เน็ต</option>
        <option value="ธุรกิจร้านขายหนังสือ">33.ธุรกิจร้านขายหนังสือ</option>
        <option value="ธุรกิจร้านขายชุดแต่งงาน">34.ธุรกิจร้านขายชุดแต่งงาน</option>
        <option value="ธุรกิจร้านขายอุปกรณ์คอมพิวเตอร์">35.ธุรกิจร้านขายอุปกรณ์คอมพิวเตอร์</option>
        <option value="ธุรกิจร้านขายอุปกรณ์ไฟฟ้า">36.ธุรกิจร้านขายอุปกรณ์ไฟฟ้า</option>
        <option value="ธุรกิจร้านขายเสื้อผ้าเด็ก">37.ธุรกิจร้านขายเสื้อผ้าเด็ก</option>
        <option value="ธุรกิจขายรถยนต์มือสอง">38.ธุรกิจขายรถยนต์มือสอง</option>
        <option value="ธุรกิจร้านขายรถจักรยานยนต์">39.ธุรกิจร้านขายรถจักรยานยนต์</option>
        <option value="ธุรกิจร้านขายรถจักรยาน">40.ธุรกิจร้านขายรถจักรยาน</option>
        <option value="ธุรกิจปั้มน้ำมัน">41.ธุรกิจปั้มน้ำมัน</option>
        <option value="ธุรกิจร้านขายรองเท้า">42.ธุรกิจร้านขายรองเท้า</option>
        <option value="ธุรกิจรับจัดงานเลี้ยง">43.ธุรกิจรับจัดงานเลี้ยง</option>
        <option value="ธุรกิจซ่อมรถยนต์">44.ธุรกิจซ่อมรถยนต์</option>
        <option value="ธุรกิจขายอุปกรณ์กีฬา">45.ธุรกิจขายอุปกรณ์กีฬา</option>
        <option value="ธุรกิจขายต้นไม้">46.ธุรกิจขายต้นไม้</option>
        <option value="ธุรกิจขายเฟอร์นิเจอร์">47.ธุรกิจขายเฟอร์นิเจอร์</option>
        <option value="ธุรกิจตัดต่อวิดิโอลงยูทูป">48.ธุรกิจตัดต่อวิดิโอลงยูทูป</option>
        <option value="ธุรกิจขายโทรศัพท์มือถือ">49.ธุรกิจขายโทรศัพท์มือถือ</option>
        <option value="ธุรกิจขายอุปกรณ์ตกแต่งบ้าน">50.ธุรกิจขายอุปกรณ์ตกแต่งบ้าน</option>
      </select>

      <p>ตำแหน่งในทีม :</p>
      <select type="number" v-model="position" required>
        <option value>- เลือกตำแหน่งในทีม -</option>
        <option value="1">ประธาน</option>
        <option value="2">รองประธาน</option>
        <option value="3">กรรมการ1</option>
        <option value="4">กรรมการ2</option>
        <option value="5">กรรมการ3</option>
        <option value="6">กรรมการ4</option>
      </select>

      <h3>ประธาน</h3>คำนำหน้านาม :
      <label>
        <input type="radio" name="titlename" value="ด.ญ." v-model="profiles.titlename" required>ด.ญ.
      </label>
      <label>
        <input type="radio" name="titlename" value="ด.ช." v-model="profiles.titlename">ด.ช.
      </label>

      <p>ชื่อจริง (ไม่ต้องใส่ คำนำหน้านาม) :</p>
      <input
        type="text"
        class="form-control"
        required
        v-model="profiles.firstname"
        placeholder="ชื่อจริง"
      >
      <p>นามสกุล :</p>
      <input
        type="text"
        class="form-control"
        required
        v-model="profiles.lastname"
        placeholder="นามสกุล"
      >

      <p>เลขที่ :</p>
      <input
        type="number"
        class="form-control"
        required
        v-model="profiles.numberinclassroom"
        min="1"
        max="99"
        placeholder="เลขที่"
      >

      <h3>คำตอบ :</h3>
      <textarea rows="15" v-model="text" required placeholder="คำตอบ"></textarea>


      <br>
      <br>
      <input type="submit" value="ส่งคำตอบ">
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      group: "",
      namebusiness: "",
      position: "",
      profiles: {
        titlename: "",
        firstname: "",
        lastname: "",
        numberinclassroom: ""
      },
      text: ""

    };
  },
  methods: {
    onSubmit() {
      axios.post("https://newapi-ntsurin.herokuapp.com/technopreneur", {
        group: this.group,
        namebusiness: this.namebusiness,
        position: this.position,
        profiles: this.profiles,
        text: this.text,


        null: (this.group = ""),
        null: (this.namebusiness = ""),
        null: (this.position = ""),
        null: (this.profiles = ""),
        null: (this.text = ""),

      });
      alert("ส่งข้อมูลเรียบร้อยแล้ว");
    }
  }
};
</script>

<style scoped>
input[type="number"],
input[type="text"],
select,
textarea {
  border: 1px solid #e0e0e0;
  padding: 0.85em 0.75em 0.75em 0.75em;
  width: 100%;
  box-sizing: border-box;
  resize: none;
  background: white;
}

input[type="submit"] {
  background-color: #0987ee;
  border: 1px solid #0987ee;
  color: #ffffff;
  font-size: 1em;
  letter-spacing: 0.025em;
  padding: 0.85em 0.75em 0.75em 0.75em;
  width: 100%;
}
input[type="radio"] {
  height: 12px;
  width: 25px;
  transform: scale(1.2);
}
</style>