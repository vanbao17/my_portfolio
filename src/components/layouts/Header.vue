<script setup lang="ts">
import Button from "../common/Button.vue";
import cvFile from "../../assets/files/cv.pdf";
const downloadCV = () => {
  const link = document.createElement("a");
  link.href = cvFile;
  link.download = "CV_Của_Tớ_Đây.pdf";
  link.click();
};
</script>
<template>
  <div class="wrapper_header">
    <div class="container_header">
      <div class="header_logo"><a href="/">BẢO</a></div>
      <ul class="header_left">
        <li>
          <a>Trang chủ</a>
        </li>
        <li>
          <a href="#block_first">Thông tin về tôi</a>
        </li>
        <li>
          <a href="#block_skill">Kỹ năng</a>
        </li>
        <li>
          <a href="#block_project">Dự án cá nhân</a>
        </li>
        <li>
          <a href="#footer">Liên hệ</a>
        </li>
      </ul>
      <div class="header_right">
        <Button
          @click="downloadCV"
          type="primary"
          title="Tải CV của tớ tại đây"
        />
      </div>
    </div>
  </div>
</template>
<style scoped lang="scss">
@media (max-width: 768px) {
  .container_header {
    width: 100% !important;
    padding: 12px 0px !important;
  }
  .header_logo {
    display: none;
  }
  .header_left {
    width: fit-content !important;
  }
  .header_right,
  .header_logo {
    display: none !important;
  }
  ul {
    margin: 0px auto;
  }
}
.wrapper_header {
  width: 100%;
  .container_header {
    width: 80%;
    margin: 0px auto;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 6px 12px;
    .header_logo {
      width: 20%;
      a {
        font-weight: 700;
        color: var(--primary-color);
        font-size: 30px;
        cursor: pointer;
      }
    }
    .header_left {
      width: 60%;
      display: flex;
      align-items: center;
      justify-content: center;
      li {
        padding: 6px 12px;
        cursor: pointer;
      }
      a {
        color: black;
        font-size: 16px;
        transition: 0.25s;
      }
      a:hover {
        color: var(--primary-color);
        filter: drop-shadow(0 0 2em var(--primary-color));
      }
    }
    .header_right {
      flex: 1;
      display: flex;
      align-items: flex-end;
      justify-content: flex-end;
    }
  }
}
</style>
