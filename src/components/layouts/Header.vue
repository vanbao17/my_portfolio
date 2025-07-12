<script setup lang="ts">
import Button from "../common/Button.vue";
import cvFile from "../../assets/files/cv.pdf";
import { ref } from "vue";

const downloadCV = () => {
  const link = document.createElement("a");
  link.href = cvFile;
  link.download = "CV_Của_Tớ_Đây.pdf";
  link.click();
};

const isMenuOpen = ref(false);

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

const closeMenu = () => {
  isMenuOpen.value = false;
};

// Thêm sự kiện lắng nghe resize để đóng menu khi chuyển từ mobile sang desktop
if (typeof window !== "undefined") {
  window.addEventListener("resize", () => {
    if (window.innerWidth > 768 && isMenuOpen.value) {
      isMenuOpen.value = false;
    }
  });
}
</script>
<template>
  <div class="wrapper_header">
    <div class="container_header">
      <div class="header_logo"><a href="/">BẢO</a></div>

      <!-- Hamburger menu button cho mobile -->
      <div class="hamburger-menu" @click="toggleMenu">
        <div class="bar" :class="{ active: isMenuOpen }"></div>
        <div class="bar" :class="{ active: isMenuOpen }"></div>
        <div class="bar" :class="{ active: isMenuOpen }"></div>
      </div>

      <!-- Menu navigation -->
      <ul class="header_left" :class="{ 'mobile-menu-open': isMenuOpen }">
        <li>
          <a @click="closeMenu">Trang chủ</a>
        </li>
        <li>
          <a href="#block_first" @click="closeMenu">Thông tin về tôi</a>
        </li>
        <li>
          <a href="#block_skill" @click="closeMenu">Kỹ năng</a>
        </li>
        <li>
          <a href="#block_project" @click="closeMenu">Dự án cá nhân</a>
        </li>
        <li>
          <a href="../pages/Services.html" >Dịch vụ</a>
        </li>
        <li>
          <a href="#footer" @click="closeMenu">Liên hệ</a>
        </li>
        <!-- Button tải CV sẽ hiển thị trong menu mobile -->
        <li class="mobile-download-button">
          <Button @click="downloadCV" type="primary" title="Tải CV của tớ" />
        </li>
      </ul>

      <div class="header_right">
        <Button
          @click="downloadCV"
          type="primary"
          title="Tải CV của tớ tại đây"
        />
      </div>
    </div>
  </div>
</template>
<style scoped lang="scss">
.wrapper_header {
  width: 100%;
  position: sticky;
  top: 0;
  z-index: 100;
  background-color: white;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);

  .container_header {
    width: 80%;
    margin: 0px auto;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 8px 12px;

    .header_logo {
      width: auto;
      a {
        font-weight: 700;
        color: var(--primary-color);
        font-size: 30px;
        cursor: pointer;
      }
    }

    .header_left {
      display: flex;
      align-items: center;
      justify-content: center;
      transition: all 0.3s ease;

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

      .mobile-download-button {
        display: none;
      }
    }

    .header_right {
      display: flex;
      align-items: center;
      justify-content: flex-end;
    }

    .hamburger-menu {
      display: none;
      flex-direction: column;
      cursor: pointer;
      z-index: 1000;

      .bar {
        width: 25px;
        height: 3px;
        background-color: #333;
        margin: 3px 0;
        transition: 0.3s;

        &.active:nth-child(1) {
          transform: rotate(-45deg) translate(-5px, 6px);
        }

        &.active:nth-child(2) {
          opacity: 0;
        }

        &.active:nth-child(3) {
          transform: rotate(45deg) translate(-5px, -6px);
        }
      }
    }
  }
}

/* Tablet styles */
@media (max-width: 1024px) {
  .wrapper_header .container_header {
    width: 90%;

    .header_logo a {
      font-size: 24px;
    }

    .header_left li {
      padding: 6px 8px;

      a {
        font-size: 14px;
      }
    }
  }
}

/* Mobile styles */
@media (max-width: 768px) {
  .wrapper_header {
    .container_header {
      width: 90%;
      padding: 12px 16px !important;
      position: relative;

      .header_logo {
        display: block !important;
        width: auto;

        a {
          font-size: 22px;
        }
      }

      .header_right {
        display: none !important;
      }

      .hamburger-menu {
        display: flex;
      }

      .header_left {
        position: fixed;
        top: 0;
        right: -100%;
        width: 70% !important;
        height: 100vh;
        background-color: white;
        flex-direction: column;
        align-items: flex-start;
        justify-content: flex-start;
        padding-top: 60px;
        box-shadow: -5px 0 15px rgba(0, 0, 0, 0.1);
        transition: right 0.3s ease;
        z-index: 99;

        &.mobile-menu-open {
          right: 0;
        }

        li {
          width: 100%;
          padding: 15px 20px;
          border-bottom: 1px solid #f1f1f1;

          a {
            font-size: 16px;
            display: block;
            width: 100%;
          }
        }

        .mobile-download-button {
          display: block;
          margin-top: 20px;
          padding: 15px 20px;
          width: 100%;

          button {
            width: 100%;
          }
        }
      }
    }
  }
}

/* Small mobile styles */
@media (max-width: 480px) {
  .wrapper_header .container_header {
    padding: 10px !important;

    .header_left {
      width: 80% !important;
    }
  }
}
</style>
