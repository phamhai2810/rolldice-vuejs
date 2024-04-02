<template>
  <div class="wrapper-popup" v-bind:class="getClassPopup">
    <div class="rule">
      <h3>Luật Chơi</h3>
      <span>
        <p style="color: green">
          *Cả 2 người chơi sẽ thống nhất số điểm để chiến thắng thông qua việc
          nhập vào ô "Final Score".
        </p>
        <br />
        <br />
        <p style="color: green">*Điều kiện để chiến thắng:</p>
        người chơi cần đạt đủ số điểm mà cả 2 đã thống nhất ở Final Score, khi 1
        người chơi đạt số điểm bằng với điểm Final thì người chơi đó sẽ chiến
        thắng.
        <br />
        <br />
        <p style="color: green">*Nguyên tắc của trò chơi:</p>
        - Người chơi sẽ Roll Dice, điểm sẽ được tổng lại ở ô Current Score, nếu
        người chơi không hài lòng với mức điểm đó, người chơi sẽ có thể Roll
        Dice 1 lần nữa.
        <br />
        - Điểm số sẽ được cộng vào điểm chính của người chơi nếu người chơi lựa
        chọn Hold điểm.
        <br />
        - Nếu người chơi Roll Dice vào số 1, người chơi đó sẽ
        mất lượt chơi mà không được cộng bất kì điểm nào.
      </span>
      <br>
      <button v-on:click="confirm" class="confirm">Đã Hiểu!</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "popup-rule",
  data() {
    return {};
  },
  props: {
    isOpenPopup: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    confirm() {
      this.$emit("handleConfirm");
    },
  },
  computed: {
    getClassPopup: function () {
      return {
        "open-popup": this.isOpenPopup,
      };
    },
  },
};
</script>

<style>
.wrapper-popup {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.4);
  opacity: 0;
  visibility: hidden;
  transition: all 0.3s ease;
}
.wrapper-popup.open-popup {
  opacity: 1;
  visibility: visible;
}
.rule {
  width: 350px;
  padding: 20px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%) scale(1.2);
  background-color: #fff;
  position: absolute;
  font-family: Arial, Helvetica, sans-serif;
  transition: all 0.3s ease;
}
.open-popup .rule {
  transform: translate(-50%, -50%) scale(1);
}
/* scale -> class */
.rule h3 {
  margin-bottom: 10px;
}
.rule .confirm {
  cursor: pointer;
  margin-top: 20px;
  padding: 8px 15px;
  border: 2px solid #333;
  background-color: #fff;
  transition: all 0.3s ease;
}
.rule .confirm:hover {
  color: #fff;
  background-color: #333;
}
</style>