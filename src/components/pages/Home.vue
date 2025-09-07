<script setup lang="ts">
import Button from "../common/Button.vue";
import CardItem from "../CardItem.vue";
import "animate.css";
import { ref, onMounted } from "vue";

// Animation references
const heroSection = ref(null);
const aboutSection = ref(null);
const projectSection = ref(null);
const skillSection = ref(null);
const experienceSection = ref(null);
const educationSection = ref(null);
const goalsSection = ref(null);
const contactSection = ref(null);

// Add animations on mount
onMounted(() => {
  // Hero section immediate animation
  if (heroSection.value) {
    heroSection.value.classList.add("animate__animated", "animate__fadeInUp");
  }

  // Set up intersection observer for scroll animations
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          const animationType =
            entry.target.dataset.animation || "animate__fadeInUp";
          entry.target.classList.add("animate__animated", animationType);
          observer.unobserve(entry.target);
        }
      });
    },
    { threshold: 0.1, rootMargin: "0px 0px -50px 0px" }
  );

  // Observe all sections
  [
    aboutSection.value,
    projectSection.value,
    skillSection.value,
    experienceSection.value,
    educationSection.value,
    goalsSection.value,
    contactSection.value,
  ].forEach((el) => {
    if (el) observer.observe(el);
  });
});
</script>

<template>
  <div class="portfolio-wrapper">
    <!-- Hero Section -->
    <section class="hero-section" ref="heroSection">
      <div class="hero-container">
        <div class="hero-content">
          <div class="hero-text">
            <div class="greeting">
              <span class="wave">👋</span>
              <h1>Xin chào, tôi là</h1>
            </div>
            <h2 class="name">Phạm Văn Bảo</h2>
            <div class="title-container">
              <h3 class="title-main">Front-end Developer</h3>
              <div class="title-accent"></div>
            </div>
            <p class="description">
              Là một sinh viên yêu thích và đam mê lĩnh vực phát triển
              Front-End, tôi mong muốn có cơ hội thực tập tại công ty. Với mục
              tiêu học hỏi và trao dồi kỹ năng chuyên môn, tôi hy vọng có thể
              đóng góp vào các dự án thực tế để tích lũy kinh nghiệm quý báu.
            </p>
            <div class="hero-actions">
              <Button type="primary" title="Liên hệ ngay" />
              <Button type="secondary" title="Xem Portfolio" />
            </div>
          </div>
          <div class="hero-visual">
            <div class="profile-container">
              <div class="profile-image">
                <img src="../../assets/images/profile.png" alt="Phạm Văn Bảo" />
                <div class="profile-ring"></div>
              </div>
              <div class="floating-elements">
                <div class="float-item" style="--delay: 0s">💻</div>
                <div class="float-item" style="--delay: 1s">🎨</div>
                <div class="float-item" style="--delay: 2s">⚡</div>
              </div>
            </div>
            <div class="social-links">
              <a
                href="https://www.facebook.com/bao.pam.03"
                target="_blank"
                class="social-link"
              >
                <img
                  src="../../assets/svg/facebook-svgrepo-com.svg"
                  alt="Facebook"
                />
              </a>
              <a
                href="https://www.linkedin.com/in/pha%CC%A3m-ba%CC%89o-7a7bb525a/"
                target="_blank"
                class="social-link"
              >
                <img
                  src="../../assets/svg/linkedin-color-svgrepo-com.svg"
                  alt="LinkedIn"
                />
              </a>
              <a
                href="https://github.com/vanbao17"
                target="_blank"
                class="social-link"
              >
                <img
                  src="../../assets/svg/github-142-svgrepo-com.svg"
                  alt="GitHub"
                />
              </a>
              <a
                href="https://www.youtube.com/@DFF17-11"
                target="_blank"
                class="social-link"
              >
                <img
                  src="../../assets/svg/youtube-svgrepo-com.svg"
                  alt="YouTube"
                />
              </a>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- About Section -->
    <!-- <section
      class="about-section"
      ref="aboutSection"
      data-animation="animate__fadeInLeft"
    >
      <div class="container">
        <div class="section-header">
          <h2>Về tôi</h2>
          <p>Tìm hiểu thêm về hành trình phát triển của tôi</p>
        </div>
        <div class="about-content">
          <div class="about-stats">
            <div class="stat-item">
              <div class="stat-number">2+</div>
              <div class="stat-label">Năm kinh nghiệm</div>
            </div>
            <div class="stat-item">
              <div class="stat-number">10+</div>
              <div class="stat-label">Dự án hoàn thành</div>
            </div>
            <div class="stat-item">
              <div class="stat-number">95%</div>
              <div class="stat-label">Sự hài lòng</div>
            </div>
          </div>
        </div>
      </div>
    </section> -->

    <!-- Projects Section -->
    <section
      class="projects-section"
      ref="projectSection"
      data-animation="animate__fadeInUp"
    >
      <div class="container">
        <div class="section-header">
          <h2>Dự án nổi bật</h2>
          <p>
            Một số dự án cá nhân mà tôi đã tham gia xây dựng và tích lũy kinh
            nghiệm
          </p>
        </div>
        <div class="projects-grid">
          <div class="project-card" data-animation="animate__fadeInLeft">
            <CardItem
              description="Đây là một nền tảng booking cho sân bóng đá theo thời gian thực giúp người dùng có thể đặt lịch sân bóng online nhanh chóng và tiện lợi "
              thumb="https://res.cloudinary.com/dumeexund/image/upload/v1754321725/Screenshot_2025-08-04_223510_srmd0y.png"
              title="Booking Football Website"
              posittion="Fullstack Developer"
              :techs="['Vuejs', 'NodeJs', 'Mysql', 'TypeScript']"
              :state="true"
              url="https://fbooking-vb.vercel.app/"
            />
          </div>
          <div class="project-card" data-animation="animate__fadeInLeft">
            <CardItem
              description="Đây là một nền tảng mạng xã hội được xây dựng để sinh viên trong trường có thể kết nối và tương tác với nhau thông qua các chức năng như đăng bài viết với AI phân loại ảnh nhạy cảm, like, comment, nhắn tin, chat nhóm, hệ thống kanban làm việc nhóm, quản lý phương tiện với Drive."
              thumb="https://res.cloudinary.com/dumeexund/image/upload/v1746070924/project/fmhh8ajg0qlaiccr1cwx.png"
              title="LifeLink Social Website"
              posittion="Fullstack Developer"
              :techs="['Python', 'Reactjs', 'NodeJs', 'Mysql']"
              :state="true"
              url="https://lifelink.io.vn/"
            />
          </div>
          <div class="project-card" data-animation="animate__fadeInRight">
            <CardItem
              description="Đây là một website mô phỏng lại website thương mại Sendo (sendo.vn) giúp chúng ta có thể mua sắm và không cần đến mua trực tiếp."
              thumb="https://res.cloudinary.com/dumeexund/image/upload/v1744555821/project/t3gah3ckhg2cszh7kskc.png"
              title="Sendo Clone Website"
              posittion="Fullstack Developer"
              :techs="['Reactjs', 'NodeJs', 'Mysql']"
              :state="false"
              url="https://senvb.vercel.app/"
            />
          </div>
          <!-- <div class="project-card" data-animation="animate__fadeInLeft">
            <CardItem
              description="Đây là một nền tảng thuộc môi trường của sendo và dành cho các cửa hàng có thể quản lý sản phẩm của mình, tùy chỉnh, thay đổi thông tin sản phẩm."
              thumb="https://res.cloudinary.com/dumeexund/image/upload/v1744555819/project/xu0cg2isqprza53r8hsp.png"
              title="Sendo Trang Bán"
              posittion="Fullstack Developer"
              :state="false"
              url="https://senvb-trangban.vercel.app/"
            />
          </div> -->
          <div class="project-card" data-animation="animate__fadeInLeft">
            <CardItem
              description="Đây là một nền tảng có thể nghe nhạc lúc mới bắt đầu học code và điên nhất tôi từng làm với 1k line với index.html, 2k line trong index.js còn css thì ?? :))"
              thumb="https://res.cloudinary.com/dumeexund/image/upload/v1752936741/Screenshot_2025-07-19_215211_jef71v.png"
              title="Zing Mp3 Fake"
              posittion="Fullstack Developer"
              :techs="['HTML', 'CSS', 'JS']"
              :state="false"
              url="https://vanbao17.github.io/ZingMp3-Fake-/"
            />
          </div>
        </div>
      </div>
    </section>

    <!-- Skills Section -->
    <section
      class="skills-section"
      ref="skillSection"
      data-animation="animate__fadeInUp"
    >
      <div class="container">
        <div class="section-header">
          <h2>Kỹ năng chuyên môn</h2>
          <p>Các công nghệ và kỹ năng tôi đã thành thạo</p>
        </div>
        <div class="skills-container">
          <div class="skill-category">
            <div class="category-header">
              <div class="category-icon">🎨</div>
              <h3>Front-end</h3>
            </div>
            <div class="skills-grid">
              <div class="skill-item">
                <div class="skill-info">
                  <div class="skill-icons">
                    <img src="../../assets/images/html.png" alt="HTML" />
                    <img src="../../assets/images/css.svg" alt="CSS" />
                    <img src="../../assets/images/js.png" alt="JavaScript" />
                  </div>
                  <span class="skill-name">HTML/CSS/JavaScript</span>
                </div>
                <div class="skill-progress">
                  <div class="progress-bar">
                    <div class="progress-fill" style="width: 95%"></div>
                  </div>
                  <span class="skill-percent">95%</span>
                </div>
              </div>
              <div class="skill-item">
                <div class="skill-info">
                  <div class="skill-icons">
                    <img
                      src="../../assets/images/typescript.svg"
                      alt="TypeScript"
                    />
                  </div>
                  <span class="skill-name">TypeScript</span>
                </div>
                <div class="skill-progress">
                  <div class="progress-bar">
                    <div class="progress-fill" style="width: 60%"></div>
                  </div>
                  <span class="skill-percent">60%</span>
                </div>
              </div>
              <div class="skill-item">
                <div class="skill-info">
                  <div class="skill-icons">
                    <img src="../../assets/images/reactjs.png" alt="React.js" />
                  </div>
                  <span class="skill-name">React.js</span>
                </div>
                <div class="skill-progress">
                  <div class="progress-bar">
                    <div class="progress-fill" style="width: 85%"></div>
                  </div>
                  <span class="skill-percent">85%</span>
                </div>
              </div>
              <div class="skill-item">
                <div class="skill-info">
                  <div class="skill-icons">
                    <img src="../../assets/images/vuejs.png" alt="Vue.js" />
                  </div>
                  <span class="skill-name">Vue.js</span>
                </div>
                <div class="skill-progress">
                  <div class="progress-bar">
                    <div class="progress-fill" style="width: 70%"></div>
                  </div>
                  <span class="skill-percent">70%</span>
                </div>
              </div>
            </div>
          </div>

          <div class="skill-category">
            <div class="category-header">
              <div class="category-icon">🧱</div>
              <h3>Back-end</h3>
            </div>
            <div class="skills-grid">
              <div class="skill-item">
                <div class="skill-info">
                  <div class="skill-icons">
                    <img src="../../assets/images/nodejs.png" alt="Node.js" />
                  </div>
                  <span class="skill-name">Node.js & RESTful API</span>
                </div>
                <div class="skill-progress">
                  <div class="progress-bar">
                    <div class="progress-fill" style="width: 80%"></div>
                  </div>
                  <span class="skill-percent">80%</span>
                </div>
              </div>
              <div class="skill-item">
                <div class="skill-info">
                  <div class="skill-icons">
                    <img
                      src="../../assets/images/database.svg"
                      alt="Databases"
                    />
                  </div>
                  <span class="skill-name">MySQL, SQL Server</span>
                </div>
                <div class="skill-progress">
                  <div class="progress-bar">
                    <div class="progress-fill" style="width: 60%"></div>
                  </div>
                  <span class="skill-percent">60%</span>
                </div>
              </div>
              <div class="skill-item">
                <div class="skill-info">
                  <div class="skill-icons">
                    <img
                      src="../../assets/images/expressjs.png"
                      alt="Express.js"
                    />
                  </div>
                  <span class="skill-name">Express.js</span>
                </div>
                <div class="skill-progress">
                  <div class="progress-bar">
                    <div class="progress-fill" style="width: 75%"></div>
                  </div>
                  <span class="skill-percent">75%</span>
                </div>
              </div>
            </div>
          </div>

          <div class="skill-category">
            <div class="category-header">
              <div class="category-icon">⚙️</div>
              <h3>DevOps & Khác</h3>
            </div>
            <div class="skills-grid">
              <div class="skill-item">
                <div class="skill-info">
                  <div class="skill-icons">
                    <img src="../../assets/images/devops.png" alt="DevOps" />
                  </div>
                  <span class="skill-name">Docker, VPS, Git, GitHub</span>
                </div>
                <div class="skill-progress">
                  <div class="progress-bar">
                    <div class="progress-fill" style="width: 50%"></div>
                  </div>
                  <span class="skill-percent">50%</span>
                </div>
              </div>
              <div class="skill-item">
                <div class="skill-info">
                  <div class="skill-icons">
                    <img src="../../assets/images/AI.png" alt="AI" />
                  </div>
                  <span class="skill-name">AI cơ bản (Python)</span>
                </div>
                <div class="skill-progress">
                  <div class="progress-bar">
                    <div class="progress-fill" style="width: 50%"></div>
                  </div>
                  <span class="skill-percent">50%</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Experience Section -->
    <section
      class="experience-section"
      ref="experienceSection"
      data-animation="animate__fadeInLeft"
    >
      <div class="container">
        <div class="section-header">
          <h2>Kinh nghiệm làm việc</h2>
          <p>Hành trình phát triển nghề nghiệp của tôi</p>
        </div>
        <div class="timeline">
          <div class="timeline-item">
            <div class="timeline-marker"></div>
            <div class="timeline-content">
              <div class="timeline-header">
                <h3>CTY TNHH SUCODEV</h3>
                <span class="timeline-date">10/2024 - 04/2025</span>
              </div>
              <div class="timeline-position">Intern Front-End Developer</div>
              <div class="timeline-details">
                <div class="detail-section">
                  <h4>Mô tả công việc:</h4>
                  <ul>
                    <li>
                      Tiếp xúc với Vue.js và thực hành với Vue.js và TypeScript
                    </li>
                    <li>
                      Tham gia code UI cho các chức năng liên quan đến CRUD của
                      dự án công ty
                    </li>
                    <li>
                      Tham gia fix bug có liên quan với công nghệ socket cho các
                      dự án của công ty
                    </li>
                  </ul>
                </div>
                <div class="detail-section">
                  <h4>Kết quả:</h4>
                  <ul>
                    <li>Hoàn thành các task được giao đúng hạn</li>
                    <li>Giảm tối đa bug trong ứng dụng nội bộ của công ty</li>
                    <li>
                      Tiếp cận được những kiến thức, các dịch vụ mới phục vụ cho
                      công việc
                    </li>
                  </ul>
                </div>
                <div class="project-link">
                  <a href="https://community.sucodev.net" target="_blank">
                    Xem dự án →
                  </a>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Education Section -->
    <section
      class="education-section"
      ref="educationSection"
      data-animation="animate__fadeInRight"
    >
      <div class="container">
        <div class="section-header">
          <h2>Học vấn</h2>
          <p>Nền tảng giáo dục của tôi</p>
        </div>
        <div class="education-card">
          <div class="education-icon">🎓</div>
          <div class="education-content">
            <h3>TRƯỜNG ĐẠI HỌC SƯ PHẠM KỸ THUẬT - ĐẠI HỌC ĐÀ NẴNG</h3>
            <div class="education-details">
              <div class="detail-item">
                <span class="label">Chuyên ngành:</span>
                <span class="value">Công nghệ thông tin</span>
              </div>
              <div class="detail-item">
                <span class="label">Thời gian:</span>
                <span class="value">2021 - 2025 (dự kiến)</span>
              </div>
              <div class="detail-item">
                <span class="label">GPA:</span>
                <span class="value">3.26</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Goals Section -->
    <section
      class="goals-section"
      ref="goalsSection"
      data-animation="animate__fadeInUp"
    >
      <div class="container">
        <div class="section-header">
          <h2>Mục tiêu nghề nghiệp</h2>
          <p>Định hướng phát triển trong tương lai</p>
        </div>
        <div class="goals-grid">
          <div class="goal-card short-term">
            <div class="goal-icon">🎯</div>
            <h3>Mục tiêu ngắn hạn (1-2 năm)</h3>
            <p>
              Phát triển thành Frontend Developer chuyên sâu về React và các
              công nghệ hiện đại, tạo ra các giao diện người dùng tối ưu, trực
              quan và thân thiện. Mong muốn trau dồi sâu về performance
              optimization, state management và UI/UX modern practices.
            </p>
          </div>
          <div class="goal-card long-term">
            <div class="goal-icon">🚀</div>
            <h3>Mục tiêu dài hạn (2-3 năm)</h3>
            <p>
              Phát triển thành Full-stack Developer có khả năng làm chủ toàn bộ
              quy trình phát triển từ frontend đến backend, database và
              deployment. Hướng đến việc thiết kế và xây dựng các hệ thống web
              application toàn diện, có khả năng mở rộng và bảo trì.
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section
      class="contact-section"
      ref="contactSection"
      data-animation="animate__fadeInUp"
    >
      <div class="container">
        <div class="section-header">
          <h2>Liên hệ với tôi</h2>
          <p>Hãy kết nối để tạo ra những điều tuyệt vời cùng nhau</p>
        </div>
        <div class="contact-grid">
          <div class="contact-card">
            <div class="contact-icon">📱</div>
            <h3>Số điện thoại</h3>
            <a href="tel:0904973022">0904973022</a>
          </div>
          <div class="contact-card">
            <div class="contact-icon">✉️</div>
            <h3>Email</h3>
            <a href="mailto:baopam21@gmail.com">baopam21@gmail.com</a>
          </div>
          <div class="contact-card">
            <div class="contact-icon">🐙</div>
            <h3>GitHub</h3>
            <a href="https://github.com/vanbao17" target="_blank">vanbao17</a>
          </div>
          <div class="contact-card">
            <div class="contact-icon">📍</div>
            <h3>Địa chỉ</h3>
            <p>Hải Châu, Thanh Bình, Đà Nẵng</p>
          </div>
          <div class="contact-card">
            <div class="contact-icon">📘</div>
            <h3>Facebook</h3>
            <a href="https://www.facebook.com/bao.pam.03" target="_blank"
              >Phạm Văn Bảo</a
            >
          </div>
          <div class="contact-card">
            <div class="contact-icon">💼</div>
            <h3>LinkedIn</h3>
            <a
              href="https://www.linkedin.com/in/pha%CC%A3m-ba%CC%89o-7a7bb525a"
              target="_blank"
              >Phạm Văn Bảo</a
            >
          </div>
        </div>
      </div>
    </section>
  </div>
</template>
<style>
/* Portfolio CSS với Animation */
:root {
  --primary-color: #3b82f6;
  --primary-dark: #2563eb;
  --secondary-color: #10b981;
  --accent-color: #f59e0b;
  --text-primary: #1f2937;
  --text-secondary: #6b7280;
  --text-light: #9ca3af;
  --bg-primary: #ffffff;
  --bg-secondary: #f9fafb;
  --bg-accent: #f3f4f6;
  --border-color: #e5e7eb;
  --shadow-sm: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
  --shadow-md: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
  --shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
  --shadow-xl: 0 20px 25px -5px rgba(0, 0, 0, 0.1);
  --gradient-primary: linear-gradient(135deg, #3b82f6 0%, #8b5cf6 100%);
  --gradient-secondary: linear-gradient(135deg, #10b981 0%, #059669 100%);
  --gradient-accent: linear-gradient(135deg, #f59e0b 0%, #d97706 100%);
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family:
    "Inter",
    -apple-system,
    BlinkMacSystemFont,
    "Segoe UI",
    Roboto,
    sans-serif;
  line-height: 1.6;
  color: var(--text-primary);
  background-color: var(--bg-primary);
  overflow-x: hidden;
}

.portfolio-wrapper {
  min-height: 100vh;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

/* Section Headers */
.section-header {
  text-align: center;
  margin-bottom: 60px;
  opacity: 0;
  animation: fadeInUp 0.8s ease-out forwards;
}

.section-header h2 {
  font-size: 2.5rem;
  font-weight: 700;
  color: var(--text-primary);
  margin-bottom: 16px;
  position: relative;
}

.section-header h2::after {
  content: "";
  position: absolute;
  bottom: -8px;
  left: 50%;
  transform: translateX(-50%);
  width: 60px;
  height: 4px;
  background: var(--gradient-primary);
  border-radius: 2px;
}

.section-header p {
  font-size: 1.125rem;
  color: var(--text-secondary);
  max-width: 600px;
  margin: 0 auto;
}

/* Hero Section */
.hero-section {
  min-height: 100vh;
  display: flex;
  align-items: center;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  position: relative;
  overflow: hidden;
}

.hero-section::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><defs><pattern id="grain" width="100" height="100" patternUnits="userSpaceOnUse"><circle cx="50" cy="50" r="1" fill="white" opacity="0.1"/></pattern></defs><rect width="100" height="100" fill="url(%23grain)"/></svg>');
  pointer-events: none;
}

.hero-container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.hero-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 80px;
  align-items: center;
  position: relative;
  z-index: 2;
}

.hero-text {
  color: white;
}

.greeting {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 16px;
  font-size: 1.25rem;
}

.wave {
  font-size: 2rem;
  animation: wave 2s ease-in-out infinite;
}

@keyframes wave {
  0%,
  100% {
    transform: rotate(0deg);
  }
  25% {
    transform: rotate(20deg);
  }
  75% {
    transform: rotate(-20deg);
  }
}

.hero-text h1 {
  font-size: 1.25rem;
  font-weight: 400;
  opacity: 0.9;
}

.name {
  font-size: 3.5rem;
  font-weight: 700;
  margin-bottom: 20px;
  background: linear-gradient(135deg, #ffffff 0%, #f0f9ff 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  animation: glow 3s ease-in-out infinite alternate;
}

@keyframes glow {
  0% {
    text-shadow: 0 0 20px rgba(255, 255, 255, 0.3);
  }
  100% {
    text-shadow: 0 0 30px rgba(255, 255, 255, 0.5);
  }
}

.title-container {
  position: relative;
  margin-bottom: 24px;
}

.title-main {
  font-size: 1.5rem;
  font-weight: 600;
  color: var(--accent-color);
  position: relative;
  z-index: 2;
}

.title-accent {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(
    135deg,
    rgba(245, 158, 11, 0.2) 0%,
    rgba(217, 119, 6, 0.2) 100%
  );
  border-radius: 8px;
  animation: pulse 2s ease-in-out infinite;
}

@keyframes pulse {
  0%,
  100% {
    transform: scale(1);
    opacity: 0.7;
  }
  50% {
    transform: scale(1.05);
    opacity: 1;
  }
}

.description {
  font-size: 1.125rem;
  line-height: 1.7;
  margin-bottom: 32px;
  opacity: 0.9;
}

.hero-actions {
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
}

/* Profile Container */
.hero-visual {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 40px;
}

.profile-container {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
}

.profile-image {
  position: relative;
  width: 280px;
  height: 280px;
  border-radius: 50%;
  overflow: hidden;
  border: 4px solid rgba(255, 255, 255, 0.2);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
  animation: float 6s ease-in-out infinite;
}

@keyframes float {
  0%,
  100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-20px);
  }
}

.profile-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.profile-image:hover img {
  transform: scale(1.1);
}

.profile-ring {
  position: absolute;
  top: -10px;
  left: -10px;
  right: -10px;
  bottom: -10px;
  border: 2px solid rgba(255, 255, 255, 0.3);
  border-radius: 50%;
  animation: spin 20s linear infinite;
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}

.floating-elements {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  pointer-events: none;
}

.float-item {
  position: absolute;
  font-size: 2rem;
  animation: floatAround 8s ease-in-out infinite;
  animation-delay: var(--delay);
}

.float-item:nth-child(1) {
  top: 20%;
  left: 10%;
}

.float-item:nth-child(2) {
  top: 30%;
  right: 10%;
}

.float-item:nth-child(3) {
  bottom: 20%;
  left: 20%;
}

@keyframes floatAround {
  0%,
  100% {
    transform: translateY(0px) rotate(0deg);
  }
  25% {
    transform: translateY(-20px) rotate(5deg);
  }
  50% {
    transform: translateY(-10px) rotate(-5deg);
  }
  75% {
    transform: translateY(-15px) rotate(3deg);
  }
}

.social-links {
  display: flex;
  gap: 20px;
  justify-content: center;
}

.social-link {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
  border: 1px solid rgba(255, 255, 255, 0.2);
}

.social-link:hover {
  background: rgba(255, 255, 255, 0.2);
  transform: translateY(-5px);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
}

.social-link img {
  width: 24px;
  height: 24px;
}

/* About Section */
.about-section {
  padding: 100px 0;
  background: var(--bg-secondary);
}

.about-stats {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 40px;
  margin-top: 40px;
}

.stat-item {
  text-align: center;
  padding: 30px;
  background: white;
  border-radius: 16px;
  box-shadow: var(--shadow-md);
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

.stat-item::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 4px;
  background: var(--gradient-primary);
}

.stat-item:hover {
  transform: translateY(-10px);
  box-shadow: var(--shadow-xl);
}

.stat-number {
  font-size: 3rem;
  font-weight: 700;
  color: var(--primary-color);
  margin-bottom: 8px;
  animation: countUp 2s ease-out;
}

@keyframes countUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.stat-label {
  font-size: 1.125rem;
  color: var(--text-secondary);
  font-weight: 500;
}

/* Projects Section */
.projects-section {
  padding: 100px 0;
  background: var(--bg-primary);
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 40px;
}

.project-card {
  opacity: 0;
  animation: slideInUp 0.8s ease-out forwards;
  animation-delay: 0.2s;
}

.project-card:nth-child(2) {
  animation-delay: 0.4s;
}

.project-card:nth-child(3) {
  animation-delay: 0.6s;
}

@keyframes slideInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Skills Section */
.skills-section {
  padding: 100px 0;
  background: var(--bg-secondary);
}

.skills-container {
  display: grid;
  gap: 50px;
}

.skill-category {
  background: white;
  padding: 40px;
  border-radius: 20px;
  box-shadow: var(--shadow-md);
  transition: all 0.3s ease;
}

.skill-category:hover {
  transform: translateY(-5px);
  box-shadow: var(--shadow-xl);
}

.category-header {
  display: flex;
  align-items: center;
  gap: 16px;
  margin-bottom: 30px;
}

.category-icon {
  font-size: 2rem;
  width: 60px;
  height: 60px;
  border-radius: 50%;
  background: var(--gradient-primary);
  display: flex;
  align-items: center;
  justify-content: center;
  animation: bounce 2s ease-in-out infinite;
}

@keyframes bounce {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
}

.category-header h3 {
  font-size: 1.5rem;
  font-weight: 600;
  color: var(--text-primary);
}

.skills-grid {
  display: grid;
  gap: 24px;
}

.skill-item {
  padding: 20px;
  background: var(--bg-accent);
  border-radius: 12px;
  transition: all 0.3s ease;
}

.skill-item:hover {
  background: var(--bg-secondary);
  transform: translateX(10px);
}

.skill-info {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 12px;
}

.skill-icons {
  display: flex;
  gap: 8px;
}

.skill-icons img {
  width: 24px;
  height: 24px;
  border-radius: 4px;
}

.skill-name {
  font-weight: 500;
  color: var(--text-primary);
}

.skill-progress {
  display: flex;
  align-items: center;
  gap: 12px;
}

.progress-bar {
  flex: 1;
  height: 8px;
  background: var(--border-color);
  border-radius: 4px;
  overflow: hidden;
}

.progress-fill {
  height: 100%;
  background: var(--gradient-primary);
  border-radius: 4px;
  transition: width 1s ease-out;
  animation: progressFill 2s ease-out;
}

@keyframes progressFill {
  from {
    width: 0%;
  }
}

.skill-percent {
  font-size: 0.875rem;
  font-weight: 600;
  color: var(--primary-color);
  min-width: 40px;
}

/* Experience Section */
.experience-section {
  padding: 100px 0;
  background: var(--bg-primary);
}

.timeline {
  position: relative;
  max-width: 800px;
  margin: 0 auto;
}

.timeline::before {
  content: "";
  position: absolute;
  left: 50%;
  top: 0;
  bottom: 0;
  width: 2px;
  background: var(--gradient-primary);
  transform: translateX(-50%);
}

.timeline-item {
  position: relative;
  margin-bottom: 50px;
  animation: fadeInLeft 0.8s ease-out;
}

.timeline-marker {
  position: absolute;
  left: 50%;
  top: 20px;
  width: 16px;
  height: 16px;
  background: var(--primary-color);
  border-radius: 50%;
  transform: translateX(-50%);
  box-shadow:
    0 0 0 4px white,
    0 0 0 8px var(--primary-color);
  animation: pulse 2s ease-in-out infinite;
}

.timeline-content {
  width: 45%;
  padding: 30px;
  background: white;
  border-radius: 16px;
  box-shadow: var(--shadow-md);
  position: relative;
  margin-left: 55%;
  transition: all 0.3s ease;
}

.timeline-content:hover {
  transform: translateY(-5px);
  box-shadow: var(--shadow-xl);
}

.timeline-content::before {
  content: "";
  position: absolute;
  left: -10px;
  top: 20px;
  width: 0;
  height: 0;
  border-top: 10px solid transparent;
  border-bottom: 10px solid transparent;
  border-right: 10px solid white;
}

.timeline-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 12px;
}

.timeline-header h3 {
  font-size: 1.25rem;
  font-weight: 600;
  color: var(--text-primary);
}

.timeline-date {
  font-size: 0.875rem;
  color: var(--text-light);
  background: var(--bg-accent);
  padding: 4px 12px;
  border-radius: 12px;
}

.timeline-position {
  font-size: 1rem;
  font-weight: 500;
  color: var(--primary-color);
  margin-bottom: 16px;
}

.detail-section {
  margin-bottom: 20px;
}

.detail-section h4 {
  font-size: 1rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 8px;
}

.detail-section ul {
  list-style: none;
  padding-left: 0;
}

.detail-section li {
  position: relative;
  padding-left: 20px;
  margin-bottom: 8px;
  color: var(--text-secondary);
}

.detail-section li::before {
  content: "▶";
  position: absolute;
  left: 0;
  color: var(--primary-color);
  font-size: 0.75rem;
}

.project-link a {
  color: var(--primary-color);
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s ease;
}

.project-link a:hover {
  color: var(--primary-dark);
}

/* Education Section */
.education-section {
  padding: 100px 0;
  background: var(--bg-secondary);
}

.education-card {
  max-width: 800px;
  margin: 0 auto;
  background: white;
  padding: 40px;
  border-radius: 20px;
  box-shadow: var(--shadow-md);
  display: flex;
  align-items: center;
  gap: 30px;
  transition: all 0.3s ease;
}

.education-card:hover {
  transform: translateY(-5px);
  box-shadow: var(--shadow-xl);
}

.education-icon {
  font-size: 4rem;
  width: 100px;
  height: 100px;
  background: var(--gradient-primary);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  animation: rotate 10s linear infinite;
}

@keyframes rotate {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

.education-content h3 {
  font-size: 1.5rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 20px;
}

.education-details {
  display: grid;
  gap: 12px;
}

.detail-item {
  display: flex;
  gap: 16px;
}

.detail-item .label {
  font-weight: 500;
  color: var(--text-secondary);
  min-width: 120px;
}

.detail-item .value {
  font-weight: 600;
  color: var(--text-primary);
}

/* Goals Section */
.goals-section {
  padding: 100px 0;
  background: var(--bg-primary);
}

.goals-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
  gap: 40px;
  margin-top: 40px;
}

.goal-card {
  padding: 40px;
  border-radius: 20px;
  position: relative;
  overflow: hidden;
  transition: all 0.3s ease;
  color: white;
}

.goal-card.short-term {
  background: var(--gradient-primary);
}

.goal-card.long-term {
  background: var(--gradient-secondary);
}

.goal-card::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(
    135deg,
    rgba(255, 255, 255, 0.1) 0%,
    transparent 100%
  );
  pointer-events: none;
}

.goal-card:hover {
  transform: translateY(-10px) scale(1.02);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.2);
}

.goal-icon {
  font-size: 3rem;
  margin-bottom: 20px;
  animation: bounce 2s ease-in-out infinite;
}

.goal-card h3 {
  font-size: 1.5rem;
  font-weight: 600;
  margin-bottom: 16px;
}

.goal-card p {
  line-height: 1.7;
  opacity: 0.9;
}

/* Contact Section */
.contact-section {
  padding: 100px 0;
  background: var(--bg-secondary);
}

.contact-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 30px;
  margin-top: 40px;
}

.contact-card {
  background: white;
  padding: 30px;
  border-radius: 16px;
  box-shadow: var(--shadow-md);
  text-align: center;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

.contact-card::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 4px;
  background: var(--gradient-primary);
  transform: translateX(-100%);
  transition: transform 0.3s ease;
}

.contact-card:hover::before {
  transform: translateX(0);
}

.contact-card:hover {
  transform: translateY(-5px);
  box-shadow: var(--shadow-xl);
}

.contact-icon {
  font-size: 2.5rem;
  margin-bottom: 16px;
  animation: bounce 2s ease-in-out infinite;
}

.contact-card h3 {
  font-size: 1.25rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 12px;
}

.contact-card a {
  color: var(--primary-color);
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s ease;
}

.contact-card a:hover {
  color: var(--primary-dark);
}

.contact-card p {
  color: var(--text-secondary);
  margin: 0;
}

/* Animation Classes */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes fadeInLeft {
  from {
    opacity: 0;
    transform: translateX(-30px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes fadeInRight {
  from {
    opacity: 0;
    transform: translateX(30px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

/* Responsive Design */
@media (max-width: 768px) {
  .hero-content {
    grid-template-columns: 1fr;
    gap: 40px;
    text-align: center;
  }

  .name {
    font-size: 2.5rem;
  }

  .section-header h2 {
    font-size: 2rem;
  }

  .hero-actions {
    justify-content: center;
  }

  .profile-image {
    width: 200px;
    height: 200px;
  }

  .projects-grid {
    grid-template-columns: 1fr;
  }

  .goals-grid {
    grid-template-columns: 1fr;
  }

  .timeline::before {
    left: 20px;
  }

  .timeline-marker {
    left: 20px;
  }

  .timeline-content {
    width: calc(100% - 60px);
    margin-left: 60px;
  }

  .timeline-content::before {
    left: -10px;
  }

  .education-card {
    flex-direction: column;
    text-align: center;
  }

  .contact-grid {
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  }
}

@media (max-width: 480px) {
  .container {
    padding: 0 16px;
  }

  .hero-section,
  .about-section,
  .projects-section,
  .skills-section,
  .experience-section,
  .education-section,
  .goals-section,
  .contact-section {
    padding: 60px 0;
  }

  .name {
    font-size: 2rem;
  }

  .section-header h2 {
    font-size: 1.75rem;
  }

  .hero-actions {
    flex-direction: column;
    align-items: center;
  }

  .profile-image {
    width: 160px;
    height: 160px;
  }

  .about-stats {
    grid-template-columns: 1fr;
  }

  .skill-category {
    padding: 20px;
  }

  .contact-grid {
    grid-template-columns: 1fr;
  }
}

/* Smooth scrolling */
html {
  scroll-behavior: smooth;
}

/* Custom scrollbar */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  background: var(--bg-accent);
}

::-webkit-scrollbar-thumb {
  background: var(--primary-color);
  border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
  background: var(--primary-dark);
}

/* Loading animation */
.animate__animated {
  animation-duration: 1s;
  animation-fill-mode: both;
}

.animate__fadeInUp {
  animation-name: fadeInUp;
}

.animate__fadeInLeft {
  animation-name: fadeInLeft;
}

.animate__fadeInRight {
  animation-name: fadeInRight;
}
</style>
