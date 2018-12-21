<template>
  <div>
    <form @submit.prevent="onSubmit">
      <b>ขอให้นักเรียนทุกคนตั้งใจทำให้เต็มที่ (มีคะแนน)</b>
      <p>ธุรกิจ :</p>
      <select type="text" v-model="group" required>
        <option value>- เลือกธุรกิจ -</option>
        <option value="1. ธุรกิจส่งออกมันสําปะหลัง">1.ธุรกิจส่งออกมันสําปะหลัง</option>
        <option value="2. ธุรกิจน้ำดื่ม">2.ธุรกิจน้ำดื่ม</option>
        <option value="3. ธุรกิจขายไอศครีม">3.ธุรกิจขายไอศครีม</option>
        <option value="4. ธุรกิจร้านอาหารไทย">4.ธุรกิจร้านอาหารไทย</option>
        <option value="5. ธุรกิจรถตู้รับส่งนักเรียน">5.ธุรกิจรถตู้รับส่งนักเรียน</option>
        <option value="6. ธุรกิจร้านขายตุ๊กตา">6.ธุรกิจร้านขายตุ๊กตา</option>
        <option value="7. ธุรกิจร้านถ่ายรูป">7.ธุรกิจร้านถ่ายรูป</option>
        <option value="8. ธุรกิจร้านก๋วยเตี๋ยว">8.ธุรกิจร้านก๋วยเตี๋ยว</option>
        <option value="9. ธุรกิจร้านขนมเบอเกอรี่">9.ธุรกิจร้านขนมเบอเกอรี่</option>
        <option value="10. ธุรกิจร้านกาแฟ">10.ธุรกิจร้านกาแฟ</option>
        <option value="11. ธุรกิจขายบ้าน">11.ธุรกิจขายบ้าน</option>
        <option value="12. ธุรกิจจำหน่ายจักรยานยนต์">12.ธุรกิจจำหน่ายจักรยานยนต์</option>
        <option value="13. ธุรกิจร้านอินเตอร์เน็ต">13.ธุรกิจร้านอินเตอร์เน็ต</option>
        <option value="14. ธุรกิจอาหารเสริม">14.ธุรกิจอาหารเสริม</option>
        <option value="15. ธุรกิจเครื่องเขียน">15.ธุรกิจเครื่องเขียน</option>
        <option value="16. ธุรกิจติวเตอร์">16.ธุรกิจติวเตอร์</option>
        <option value="17. ธุรกิจบริการรับส่งของในประเทศ">17.ธุรกิจบริการรับส่งของในประเทศ</option>
        <option value="18. ธุรกิจร้านอาหารจีน">18.ธุรกิจร้านอาหารจีน</option>
        <option value="19. ธุรกิจร้านตัดขนสุนัข">19.ธุรกิจร้านตัดขนสุนัข</option>
        <option value="20. ธุรกิจร้านอาหารญี่ปุ่น">20.ธุรกิจร้านอาหารญี่ปุ่น</option>
        <option value="21. ธุรกิจหอพัก">21.ธุรกิจหอพัก</option>
        <option value="22. ธุรกิจนำเข้าสินค้า">22.ธุรกิจนำเข้าสินค้า</option>
        <option value="23. ธุรกิจส่งออกสินค้า">23.ธุรกิจส่งออกสินค้า</option>
        <option value="24. ธุรกิจซ่อมบ้าน">24.ธุรกิจซ่อมบ้าน</option>
        <option value="25. ธุรกิจร้านขายเสื้อผ้าผู้หญิง">25.ธุรกิจร้านขายเสื้อผ้าผู้หญิง</option>
        <option value="26. ธุรกิจร้านขายต้นไม้">26.ธุรกิจร้านขายต้นไม้</option>
        <option value="27. ธุรกิจร้านอาหารญี่ปุ่น">27.ธุรกิจร้านอาหารญี่ปุ่น</option>
        <option value="28. ธุรกิจร้านเนื้อย่าง">28.ธุรกิจร้านเนื้อย่าง</option>
        <option value="29. ธุรกิจร้านขายยางรถยนต์">29.ธุรกิจร้านขายยางรถยนต์</option>
        <option value="30. ธุรกิจร้านขายเสื้อผ้าผู้ชาย">30.ธุรกิจร้านขายเสื้อผ้าผู้ชาย</option>
        <option value="31. ธุรกิจแปรรูปอาหาร">31.ธุรกิจแปรรูปอาหาร</option>
        <option value="32. ธุรกิจให้บริการอินเตอร์เน็ต">32.ธุรกิจให้บริการอินเตอร์เน็ต</option>
        <option value="33. ธุรกิจร้านขายหนังสือ">33.ธุรกิจร้านขายหนังสือ</option>
        <option value="34. ธุรกิจร้านขายชุดแต่งงาน">34.ธุรกิจร้านขายชุดแต่งงาน</option>
        <option value="35. ธุรกิจร้านขายอุปกรณ์คอมพิวเตอร์">35.ธุรกิจร้านขายอุปกรณ์คอมพิวเตอร์</option>
        <option value="36. ธุรกิจร้านขายอุปกรณ์ไฟฟ้า">36.ธุรกิจร้านขายอุปกรณ์ไฟฟ้า</option>
        <option value="37. ธุรกิจร้านขายเสื้อผ้าเด็ก">37.ธุรกิจร้านขายเสื้อผ้าเด็ก</option>
        <option value="38. ธุรกิจขายรถยนต์มือสอง">38.ธุรกิจขายรถยนต์มือสอง</option>
        <option value="39. ธุรกิจร้านขายรถจักรยานยนต์">39.ธุรกิจร้านขายรถจักรยานยนต์</option>
        <option value="40. ธุรกิจร้านขายรถจักรยาน">40.ธุรกิจร้านขายรถจักรยาน</option>
        <option value="41. ธุรกิจปั้มน้ำมัน">41.ธุรกิจปั้มน้ำมัน</option>
        <option value="42. ธุรกิจร้านขายรองเท้า">42.ธุรกิจร้านขายรองเท้า</option>
        <option value="43. ธุรกิจรับจัดงานเลี้ยง">43.ธุรกิจรับจัดงานเลี้ยง</option>
        <option value="44. ธุรกิจซ่อมรถยนต์">44.ธุรกิจซ่อมรถยนต์</option>
        <option value="45. ธุรกิจขายอุปกรณ์กีฬา">45.ธุรกิจขายอุปกรณ์กีฬา</option>
        <option value="46. ธุรกิจขายต้นไม้">46.ธุรกิจขายต้นไม้</option>
        <option value="47. ธุรกิจขายเฟอร์นิเจอร์">47.ธุรกิจขายเฟอร์นิเจอร์</option>
        <option value="48. ธุรกิจตัดต่อวิดิโอลงยูทูป">48.ธุรกิจตัดต่อวิดิโอลงยูทูป</option>
        <option value="49. ธุรกิจขายโทรศัพท์มือถือ">49.ธุรกิจขายโทรศัพท์มือถือ</option>
        <option value="50. ธุรกิจขายอุปกรณ์ตกแต่งบ้าน">50.ธุรกิจขายอุปกรณ์ตกแต่งบ้าน</option>
      </select>

      <p>ห้อง :</p>
      <select type="text" v-model="classroom" required>
        <option value>- เลือกห้อง -</option>
        <option value="ป.5/1">ป.5/1</option>
        <option value="ป.5/2">ป.5/2</option>
        <option value="ป.5/3">ป.5/3</option>
        <option value="ป.5/4">ป.5/4</option>
        <option value="ป.5/5">ป.5/5</option>
        <option value="ป.5/6">ป.5/6</option>
        <option value="ป.5/7">ป.5/7</option>
        <option value="ป.5/8">ป.5/8</option>
        <option value="ป.5/9">ป.5/9</option>
        <option value="ป.5/10">ป.5/10</option>
      </select>
      

      <h3>ประธาน</h3>
      คำนำหน้านาม :
      <label>
        <input type="radio" name="titlename1" value="ด.ญ." v-model="profiles.titlename1" required>ด.ญ.
      </label>
      <label>
        <input type="radio" name="titlename1" value="ด.ช." v-model="profiles.titlename1">ด.ช.
      </label>

      <p>ชื่อจริง (ไม่ต้องใส่ คำนำหน้านาม) :</p>
      <input
        type="text"
        class="form-control"
        required
        v-model="profiles.firstname1"
        placeholder="ชื่อจริง"
      >
      <p>นามสกุล :</p>
      <input
        type="text"
        class="form-control"
        required
        v-model="profiles.lastname1"
        placeholder="นามสกุล"
      >

      <p>เลขที่ :</p>
      <input
        type="number"
        class="form-control"
        required
        v-model="profiles.numberinclassroom1"
        min="1"
        max="99"
        placeholder="เลขที่"
      >

      <h3>รองประธาน</h3>
      คำนำหน้านาม :
      <label>
        <input type="radio" name="titlename2" value="ด.ญ." v-model="profiles.titlename2" required>ด.ญ.
      </label>
      <label>
        <input type="radio" name="titlename2" value="ด.ช." v-model="profiles.titlename2">ด.ช.
      </label>

      <p>ชื่อจริง (ไม่ต้องใส่ คำนำหน้านาม) :</p>
      <input
        type="text"
        class="form-control"
        required
        v-model="profiles.firstname2"
        placeholder="ชื่อจริง"
      >
      <p>นามสกุล :</p>
      <input
        type="text"
        class="form-control"
        required
        v-model="profiles.lastname2"
        placeholder="นามสกุล"
      >

      <p>เลขที่ :</p>
      <input
        type="number"
        class="form-control"
        required
        v-model="profiles.numberinclassroom2"
        min="1"
        max="99"
        placeholder="เลขที่"
      >

     <h3>กรรมการ1</h3>
      คำนำหน้านาม :
      <label>
        <input type="radio" name="titlename3" value="ด.ญ." v-model="profiles.titlename3" required>ด.ญ.
      </label>
      <label>
        <input type="radio" name="titlename3" value="ด.ช." v-model="profiles.titlename3">ด.ช.
      </label>

      <p>ชื่อจริง (ไม่ต้องใส่ คำนำหน้านาม) :</p>
      <input
        type="text"
        class="form-control"
        required
        v-model="profiles.firstname3"
        placeholder="ชื่อจริง"
      >
      <p>นามสกุล :</p>
      <input
        type="text"
        class="form-control"
        required
        v-model="profiles.lastname3"
        placeholder="นามสกุล"
      >

      <p>เลขที่ :</p>
      <input
        type="number"
        class="form-control"
        required
        v-model="profiles.numberinclassroom3"
        min="1"
        max="99"
        placeholder="เลขที่"
      >

     <h3>กรรมการ2</h3>
      คำนำหน้านาม :
      <label>
        <input type="radio" name="titlename4" value="ด.ญ." v-model="profiles.titlename4" required>ด.ญ.
      </label>
      <label>
        <input type="radio" name="titlename4" value="ด.ช." v-model="profiles.titlename4">ด.ช.
      </label>

      <p>ชื่อจริง (ไม่ต้องใส่ คำนำหน้านาม) :</p>
      <input
        type="text"
        class="form-control"
        required
        v-model="profiles.firstname4"
        placeholder="ชื่อจริง"
      >
      <p>นามสกุล :</p>
      <input
        type="text"
        class="form-control"
        required
        v-model="profiles.lastname4"
        placeholder="นามสกุล"
      >

      <p>เลขที่ :</p>
      <input
        type="number"
        class="form-control"
        required
        v-model="profiles.numberinclassroom4"
        min="1"
        max="99"
        placeholder="เลขที่"
      >

     <h3>กรรมการ3</h3>
      คำนำหน้านาม :
      <label>
        <input type="radio" name="titlename5" value="ด.ญ." v-model="profiles.titlename5" required>ด.ญ.
      </label>
      <label>
        <input type="radio" name="titlename5" value="ด.ช." v-model="profiles.titlename5">ด.ช.
      </label>

      <p>ชื่อจริง (ไม่ต้องใส่ คำนำหน้านาม) :</p>
      <input
        type="text"
        class="form-control"
        required
        v-model="profiles.firstname5"
        placeholder="ชื่อจริง"
      >
      <p>นามสกุล :</p>
      <input
        type="text"
        class="form-control"
        required
        v-model="profiles.lastname5"
        placeholder="นามสกุล"
      >

      <p>เลขที่ :</p>
      <input
        type="number"
        class="form-control"
        required
        v-model="profiles.numberinclassroom5"
        min="1"
        max="99"
        placeholder="เลขที่"
      >

     <h3>กรรมการ4</h3>
      คำนำหน้านาม :
      <label>
        <input type="radio" name="titlename6" value="ด.ญ." v-model="profiles.titlename6" required>ด.ญ.
      </label>
      <label>
        <input type="radio" name="titlename6" value="ด.ช." v-model="profiles.titlename6">ด.ช.
      </label>

      <p>ชื่อจริง (ไม่ต้องใส่ คำนำหน้านาม) :</p>
      <input
        type="text"
        class="form-control"
        required
        v-model="profiles.firstname6"
        placeholder="ชื่อจริง"
      >
      <p>นามสกุล :</p>
      <input
        type="text"
        class="form-control"
        required
        v-model="profiles.lastname6"
        placeholder="นามสกุล"
      >

      <p>เลขที่ :</p>
      <input
        type="number"
        class="form-control"
        required
        v-model="profiles.numberinclassroom6"
        min="1"
        max="99"
        placeholder="เลขที่"
      >

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
      classroom: "",
      profiles: {
        titlename: "",
        firstname: "",
        lastname: "",
        numberinclassroom: ""
      }
    };
  },
  methods: {
    onSubmit() {
      axios.post("https://newapi-ntsurin.herokuapp.com/regtechnopreneur", {
        group: this.group,
        classroom: this.classroom,
        profiles: this.profiles,
        titlename: this.titlename,
        firstname: this.firstname,
        lastname: this.lastname,
        numberinclassroom: this.numberinclassroom,

        null: (this.group = ""),
        null: (this.classroom = ""),
        null: (this.profiles = ""),
        null: (this.titlename = ""),
        null: (this.firstname = ""),
        null: (this.lastname = ""),
        null: (this.numberinclassroom = "")
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