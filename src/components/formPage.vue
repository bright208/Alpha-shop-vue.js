<template>
<div class="billing-info">
      <div class="form-container part-a">
        <h3 class="billing-title">寄送地址</h3>
        <div class="gender-container">
          <label for="">稱謂</label>
          <br>
          <select name="gender" id="">
            <option value="male" selected>先生</option>
            <option value="female">小姐</option>
          </select>
        </div>
        <div class="name-container">
          <label for="name">姓名</label>
          <br>
          <input id="name" type="text" name="name" placeholder="請輸入姓名" required>
          <span class="tick"></span>
        </div>
        <div class="phone-container">
          <label for="phone">電話</label>
          <br>
          <input id="phone" type="text" name="phone" placeholder="請輸入行動電話" pattern="[0-9]{8,10}" required>
          <span class="tick"></span>
        </div>
        <div class="email-container">
          <label for="email">Email</label>
          <br>
          <input id="email" type="email" name="email" placeholder="請輸入電子郵件" required>
          <span class="tick"></span>
        </div>

        <div class="region-container">
          <label for="region">縣市</label>
          <br>
          <select name="region" id="region">
            <option value="">請選擇縣市</option>
            <option value="Keelung">基隆市</option>
            <option value="Taipei">台北市</option>
            <option value="New Taipei">新北市</option>
            <option value="Taoyuan">桃園市</option>
            <option value="Taichung">臺中市</option>
            <option value="Tainan">臺南市</option>
            <option value="Kaohsiung">高雄市</option>
            <option value="Ilan">宜蘭縣</option>
          </select>
        </div>
        <div class="address-container">
          <label for="address">地址</label>
          <br>
          <input id="address" type="address" name="address" placeholder="請輸入地址" required>
          <span class="tick"></span>
        </div>
      </div>
    </div>


</template>