<script setup lang="ts">
const currentYear = new Date().getFullYear();
</script>

<template>
  <footer class="footer" id="footer">
    <div class="footer-content">
      <!-- Logo -->
      <!-- <div class="logo">
        <img src="@/assets/logo.png" alt="FawziUiUx" class="logo-img" />
      </div> -->

      <!-- Menu -->
      <nav class="menu">
        <a href="#">Home</a>
        <a href="#">About Me</a>
        <a href="#">Services</a>
        <a href="#">Projects</a>
        <a href="#">Testimonials</a>
        <a href="#">Contact</a>
      </nav>

      <!-- Social Icons -->
      <div class="social-icons">
        <a href="#"><img src="../../assets//icons/facebook.svg" /></a>
        <a href="#"><img src="../../assets//icons/github.svg" /></a>
        <a href="#"><img src="../../assets//icons/linkedin.svg" /></a>
      </div>
    </div>

    <!-- Copyright -->
    <div class="copyright">
      © {{ currentYear }} <span class="highlight">Phạm Văn Bảo</span> All
      Rights Reserved, Inc.
    </div>
  </footer>
</template>

<style scoped lang="scss">
.footer {
  background-color: #f8f8f8;
  width: 100%;
  text-align: center;
}
img {
  width: 24px;
  height: 24px;
}
.footer-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px 0;
  gap: 10px;
}

.logo-img {
  height: 50px;
}

.menu {
  display: flex;
  gap: 15px;
  font-size: 16px;
}

.menu a {
  text-decoration: none;
  color: #000;
  font-weight: 500;
}

.social-icons {
  display: flex;
  gap: 15px;
  font-size: 20px;
}

.social-icons a {
  color: #000;
}

.copyright {
  margin-top: 10px;
  background-color: #333;
  color: white;
  padding: 10px 0;
  font-size: 14px;
}

.highlight {
  color: #ff7b00;
  font-weight: bold;
}
</style>
