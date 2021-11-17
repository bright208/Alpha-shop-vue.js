<template>

<div class="billing-info">
      <div class="form-container part-c">
        <h3 class="billing-title">付款資訊</h3>
        <div class="cardholder-container">
          <label for="cardholder">持卡人姓名</label>
          <br>
          <input id="cardholder" type="text" placeholder="John Doe" name="cardholder" required>
          <span class="tick"></span>
        </div>
        <div class="cardnumber-container">
          <label for="cardnumber">卡號</label>
          <br>
          <input id="cardnumber" type="text" placeholder="1111 2222 3333 4444" name="cardnumber" pattern="[0-9]{16}" required>
          <span class="tick"></span>
        </div>
        <div class="expiry-date-container" required>
          <label for="expiry-date">有效期限</label>
          <br>
          <input id="expiry-date" type="text" placeholder="MM/YY" name="expiry-date" required>
          <span class="tick"></span>
        </div>
        <div class="cvc-container">
          <label for="cvc">CVC/CCV</label>
          <br>
          <input id="cvc" type="text" placeholder="123" name="cvc" required>
          <span class="tick"></span>
        </div>
      </div>
    </div>

</template>