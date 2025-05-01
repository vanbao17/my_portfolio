<script setup lang="ts">
import Button from "../common/Button.vue";
import CardItem from "../CardItem.vue";
import "animate.css";
import { ref, onMounted } from "vue";
const animatedDiv1 = ref(HTMLDivElement | null);
const animatedDiv2 = ref(HTMLDivElement | null);
const animatedDiv3 = ref(HTMLDivElement | null);
const animatedDiv4 = ref(HTMLDivElement | null);
// const animatedDiv5 = ref(HTMLDivElement | null);
const animatedDiv5 = ref(null);
// Animation references
const animatedExperience = ref(null);
const animatedEducation = ref(null);
const animatedGoals = ref(null);
const animatedContact = ref(null);

// Add animations on mount
onMounted(() => {
  // Add animation classes to all new sections
  if (animatedExperience.value) {
    animatedExperience.value.classList.add(
      "animate__animated",
      "animate__fadeInUp"
    );
  }

  if (animatedEducation.value) {
    animatedEducation.value.classList.add(
      "animate__animated",
      "animate__fadeInUp"
    );
  }

  if (animatedGoals.value) {
    animatedGoals.value.classList.add("animate__animated", "animate__fadeInUp");
  }

  if (animatedContact.value) {
    animatedContact.value.classList.add(
      "animate__animated",
      "animate__fadeInUp"
    );
  }

  // Set up scroll-based animations
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add("animate__animated", "animate__fadeInUp");
          observer.unobserve(entry.target);
        }
      });
    },
    { threshold: 0.2 }
  );

  // Observe all new sections
  [
    animatedExperience.value,
    animatedEducation.value,
    animatedGoals.value,
    animatedContact.value,
  ].forEach((el) => {
    if (el) observer.observe(el);
  });
});
onMounted(() => {
  if (
    animatedDiv1.value &&
    animatedDiv2.value &&
    animatedDiv3.value &&
    animatedDiv4.value &&
    animatedDiv5.value
  ) {
    animatedDiv1.value?.classList.add(
      "animate__animated",
      "animate__fadeInLeft"
    );
    animatedDiv2.value?.classList.add(
      "animate__animated",
      "animate__fadeInRight"
    );
    animatedDiv3.value?.classList.add(
      "animate__animated",
      "animate__fadeInLeft"
    );
    animatedDiv4.value?.classList.add(
      "animate__animated",
      "animate__fadeInRight"
    );
    animatedDiv5.value?.classList.add(
      "animate__animated",
      "animate__slideInUp"
    );
  }
});
</script>

<template>
  <div class="wrapper_home">
    <div class="container_home">
      <div class="block_first" id="block_first">
        <div class="block_first_left" ref="animatedDiv1">
          <div class="block_infor">
            <p class="text_1">Hi I am</p>
            <p class="text_2">Phạm Văn Bảo</p>
            <p class="text_3">Front-end</p>
            <p class="text_4">Developer</p>
          </div>
          <div class="block_description">
            <span
              >Là một sinh viên yêu thích và đam mê lĩnh vực phát triển
              Front-End, tôi mong muốn có cơ hội thực tập tại công ty. Với mục
              tiêu là học hỏi và trao dồi kỹ năng chuyên môn , bên cạnh đó tôi
              hy vọng có thể đóng góp vào các dự án thực tế của công ty để có
              thể tích lũy những kinh nghiệm quý báu từ các chuyên gia tại công
              ty.
            </span>
          </div>
          <!-- <Button type="primary" title="Hire Me"></Button> -->
        </div>
        <div class="block_first_right" ref="animatedDiv2">
          <div class="block_thumb">
            <img src="../../assets/images/profile.png" />
          </div>
          <div class="block_social_infor">
            <div class="icon">
              <a target="_blank" href="https://www.facebook.com/bao.pam.03"
                ><img src="../../assets/icons/facebook.svg"
              /></a>
            </div>
            <div class="icon">
              <a
                target="_blank"
                href="https://www.linkedin.com/in/pha%CC%A3m-ba%CC%89o-7a7bb525a/"
                ><img src="../../assets/icons/linkedin.svg"
              /></a>
            </div>
            <div class="icon">
              <a href="https://github.com/vanbao17" target="_blank"
                ><img src="../../assets/icons/github.svg"
              /></a>
            </div>
          </div>
        </div>
      </div>
      <div class="block_project" ref="animatedDiv5" id="block_project">
        <h1>Dự án cá nhân</h1>
        <p>
          Một số dự án cá nhân, mà bản thân đã tham gia xây dựng và tích lũy
          được khá nhiều kinh nghiệm.
        </p>
        <!-- <div class="buttons">
          <Button type="primary" title="Website"></Button>
        </div> -->
        <div class="cards">
          <div ref="animatedDiv3">
            <CardItem
              description="Đây là một nền tảng mạng xã hội được xây dựng để sinh viên trong trường có thể kết nối và tương tác với nhau thông qua các chức năng cơ bản như đăng bài viết, like, comment ,nhắn tin và làm việc nhóm. Sinh viên trong trường có thể đăng nhập bắt đầu chia sẽ cảm nghĩ cũng như trao đổi file học tập ."
              thumb="https://res.cloudinary.com/dumeexund/image/upload/v1746070924/project/fmhh8ajg0qlaiccr1cwx.png"
              title="LifeLink Social Website"
              posittion="Fullstack Developer"
              :state="true"
              url="https://lifelink.io.vn/"
            ></CardItem>
          </div>
          <div ref="animatedDiv4">
            <CardItem
              description="Đây là một website mô phỏng lại website thương mại Sendo (sendo.vn) giúp chúng ta có thể mua sắm và không cần đến mua trực tiếp ."
              thumb="https://res.cloudinary.com/dumeexund/image/upload/v1744555821/project/t3gah3ckhg2cszh7kskc.png"
              title="Sendo Clone Website"
              posittion="Fullstack Developer"
              :state="false"
              url="https://senvb.vercel.app/"
            ></CardItem>
          </div>
          <div ref="animatedDiv5">
            <CardItem
              description="Đây là một nền tảng thuộc môi trường của sendo và dành cho các cửa hàng có thể quản lý sản phẩm của mình, tùy chỉnh, thay đổi thông tin sản phẩm"
              thumb="https://res.cloudinary.com/dumeexund/image/upload/v1744555819/project/xu0cg2isqprza53r8hsp.png"
              title="Sendo Trang Bán"
              posittion="Fullstack Developer"
              :state="true"
              url="https://senvb-trangban.vercel.app/"
            ></CardItem>
          </div>
        </div>
        <div></div>
      </div>
      <div class="block_skill" id="block_skill" ref="animatedDiv5">
        <h2>Kỹ năng</h2>
        <div class="skill_category">
          <h3>🎨 Front-end</h3>
          <ul class="skills_list">
            <li>
              <div class="container-skill">
                <div class="title">
                  <img src="../../assets/images/html.png" alt="Html" />
                  <img src="../../assets/images/css.svg" alt="Css" />
                  <img src="../../assets/images/js.png" alt="Javascript" />
                  <span>HTML/CSS/SCSS/JavaScript</span>
                  <div class="percent">
                    <span>95%</span>
                  </div>
                </div>
                <div class="progress-bar">
                  <div class="progress" style="width: 95%"></div>
                </div>
              </div>
            </li>
            <li>
              <div class="container-skill">
                <div class="title">
                  <img
                    src="../../assets/images/typescript.svg"
                    alt="TypeScript"
                  />
                  <span>TypeScript</span>
                  <div class="percent">
                    <span>60%</span>
                  </div>
                </div>
                <div class="progress-bar">
                  <div class="progress" style="width: 60%"></div>
                </div>
              </div>
            </li>
            <li>
              <div class="container-skill">
                <div class="title">
                  <img src="../../assets/images/reactjs.png" alt="React.js" />
                  <span>React.js</span>
                  <div class="percent">
                    <span>85%</span>
                  </div>
                </div>
                <div class="progress-bar">
                  <div class="progress" style="width: 85%"></div>
                </div>
              </div>
            </li>
            <li>
              <div class="container-skill">
                <div class="title">
                  <img src="../../assets/images/vuejs.png" alt="Vue.js" />
                  <span>Vue.js</span>
                  <div class="percent">
                    <span>70%</span>
                  </div>
                </div>
                <div class="progress-bar">
                  <div class="progress" style="width: 70%"></div>
                </div>
              </div>
            </li>
          </ul>
        </div>

        <div class="skill_category">
          <h3>🧱 Back-end</h3>
          <ul class="skills_list">
            <li>
              <div class="container-skill">
                <div class="title">
                  <img src="../../assets/images/nodejs.png" alt="Node.js" />
                  <span>Node.js & RESTful API</span>
                  <div class="percent">
                    <span>80%</span>
                  </div>
                </div>
                <div class="progress-bar">
                  <div class="progress" style="width: 80%"></div>
                </div>
              </div>
            </li>
            <li>
              <div class="container-skill">
                <div class="title">
                  <img src="../../assets/images/database.svg" alt="Databases" />
                  <span>MySQL, SQL Server</span>
                  <div class="percent">
                    <span>60%</span>
                  </div>
                </div>
                <div class="progress-bar">
                  <div class="progress" style="width: 60%"></div>
                </div>
              </div>
            </li>
            <li>
              <div class="container-skill">
                <div class="title">
                  <img
                    src="../../assets/images/expressjs.png"
                    alt="Express.js"
                  />
                  <span>Express.js</span>
                  <div class="percent">
                    <span>75%</span>
                  </div>
                </div>
                <div class="progress-bar">
                  <div class="progress" style="width: 75%"></div>
                </div>
              </div>
            </li>
          </ul>
        </div>

        <div class="skill_category">
          <h3>⚙️ DevOps & Khác</h3>
          <ul class="skills_list">
            <li>
              <div class="container-skill">
                <div class="title">
                  <img src="../../assets/images/devops.png" alt="DevOps" />
                  <span>Docker, VPS, Git, GitHub, Github Action</span>
                  <div class="percent">
                    <span>50%</span>
                  </div>
                </div>
                <div class="progress-bar">
                  <div class="progress" style="width: 50%"></div>
                </div>
              </div>
            </li>
            <li>
              <div class="container-skill">
                <div class="title">
                  <img src="../../assets/images/AI.png" alt="AI" />
                  <span>AI cơ bản (Python, nhận diện ảnh nhạy cảm)</span>
                  <div class="percent">
                    <span>50%</span>
                  </div>
                </div>
                <div class="progress-bar">
                  <div class="progress" style="width: 50%"></div>
                </div>
              </div>
            </li>
          </ul>
        </div>
      </div>
      <div
        class="block_experience"
        id="block_experience"
        ref="animatedExperience"
      >
        <h2>Kinh Nghiệm Làm Việc</h2>
        <div class="experience_item">
          <div class="exp_header">
            <div class="company_info">
              <h3>CTY TNHH SUCODEV</h3>
              <span class="duration">10/2024 - 04/2025</span>
            </div>
            <div class="position">Intern Front-End Developer</div>
          </div>
          <div class="exp_content">
            <div class="responsibilities">
              <h4>Mô tả công việc:</h4>
              <ul>
                <li>
                  Tiếp xúc với vuejs và thực hành với Vuejs và Typescript.
                </li>
                <li>
                  Tham gia code UI cho các chức năng liên quan đến CRUD của dự
                  án công ty.
                </li>
                <li>
                  Tham gia fix bug có liên quan với công nghệ socket cho các dự
                  án của công ty và website nội bộ của công ty.
                </li>
              </ul>
            </div>
            <div class="achievements">
              <h4>Kết quả:</h4>
              <ul>
                <li>Hoàn thành các task được giao đúng hạn.</li>
                <li>Giảm tối đa bug trong ứng dụng nội bộ của công ty.</li>
                <li>
                  Tiếp cận được những kiến thức, các dịch vụ mới phục vụ cho
                  công việc.
                </li>
              </ul>
            </div>
            <div class="projects">
              <h4>Các dự án tham gia:</h4>
              <a href="https://community.sucodev.net" target="_blank"
                >https://community.sucodev.net</a
              >
            </div>
          </div>
        </div>
      </div>

      <!-- Education Section -->
      <div class="block_education" id="block_education" ref="animatedEducation">
        <h2>Học Vấn</h2>
        <div class="education_item">
          <div class="school_info">
            <h3>TRƯỜNG ĐẠI HỌC SƯ PHẠM KỸ THUẬT - ĐẠI HỌC ĐÀ NẴNG</h3>
            <span class="duration">2021 - 2025 (dự kiến)</span>
          </div>
          <div class="edu_details">
            <p><strong>Chuyên ngành:</strong> Công nghệ thông tin</p>
            <p><strong>GPA (hiện tại):</strong> 3.19</p>
          </div>
        </div>
      </div>

      <!-- Career Goals Section -->
      <div class="block_goals" id="block_goals" ref="animatedGoals">
        <h2>Mục Tiêu Nghề Nghiệp</h2>
        <div class="goals_container">
          <div class="goal_item short_term">
            <h3>Mục tiêu ngắn hạn (1-2 năm)</h3>
            <p>
              Phát triển thành Frontend Developer chuyên sâu về React và các
              công nghệ hiện đại, tạo ra các giao diện người dùng tối ưu, trực
              quan và thân thiện. Mong muốn trau dồi sâu về performance
              optimization, state management và UI/UX modern practices.
            </p>
          </div>
          <div class="goal_item long_term">
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

      <!-- Contact Section -->
      <div class="block_contact" id="block_contact" ref="animatedContact">
        <h2>Liên Hệ</h2>
        <div class="contact_container">
          <div class="contact_item">
            <div class="icon">
              <img src="../../assets/svg/phone.svg" alt="Phone" />
            </div>
            <div class="info">
              <h3>Số điện thoại</h3>
              <a href="tel:0904973022">0904973022</a>
            </div>
          </div>
          <div class="contact_item">
            <div class="icon">
              <img src="../../assets/svg/email.svg" alt="Email" />
            </div>
            <div class="info">
              <h3>Email</h3>
              <a href="mailto:baopam21@gmail.com">baopam21@gmail.com</a>
            </div>
          </div>
          <div class="contact_item">
            <div class="icon">
              <img src="../../assets/icons/github.svg" alt="Github" />
            </div>
            <div class="info">
              <h3>Github</h3>
              <a href="https://github.com/vanbao17" target="_blank">vanbao17</a>
            </div>
          </div>
          <div class="contact_item">
            <div class="icon">
              <img src="../../assets/svg/location.svg" alt="Location" />
            </div>
            <div class="info">
              <h3>Địa chỉ</h3>
              <p>Hải Châu, Thanh Bình, Đà Nẵng</p>
            </div>
          </div>
          <div class="contact_item">
            <div class="icon">
              <img src="../../assets/icons/facebook.svg" alt="Location" />
            </div>
            <div class="info">
              <h3>Facebook</h3>
              <a href="https://www.facebook.com/bao.pam.03" target="_blank"
                >Phạm Văn Bảo</a
              >
            </div>
          </div>
          <div class="contact_item">
            <div class="icon">
              <img src="../../assets/icons/linkedin.svg" alt="Location" />
            </div>
            <div class="info">
              <h3>Linkedin</h3>
              <a
                href="https://www.linkedin.com/in/pha%CC%A3m-ba%CC%89o-7a7bb525a"
                target="_blank"
                >Phạm Văn Bảo</a
              >
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.wrapper_home {
  width: 100%;
}
/* Common section styling */
.block_experience,
.block_education,
.block_goals,
.block_contact {
  padding: 2rem;
  border-radius: 8px;
  background-color: #f8f9fa;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  max-width: 800px;
  margin: 4rem auto;
}

h2 {
  text-align: center;
  margin-bottom: 1.5rem;
  color: #2c3e50;
  font-size: 2rem;
}

/* Experience Section */
.experience_item {
  margin-bottom: 1.5rem;
  border-left: 3px solid #42b883;
  padding-left: 1.5rem;
}

.exp_header {
  margin-bottom: 1rem;
}

.company_info {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 0.5rem;

  h3 {
    color: #42b883;
    font-size: 1.3rem;
    font-weight: 600;
  }

  .duration {
    color: #34495e;
    font-weight: 500;
  }
}

.position {
  font-weight: 500;
  color: #2c3e50;
  font-size: 1.1rem;
}

.exp_content {
  h4 {
    color: #34495e;
    margin-bottom: 0.5rem;
    font-size: 1.1rem;
  }

  ul {
    padding-left: 1.5rem;
    margin-bottom: 1rem;

    li {
      margin-bottom: 0.5rem;
    }
  }
}

.projects {
  a {
    color: #42b883;
    text-decoration: none;
    font-weight: 500;
    transition: color 0.3s;

    &:hover {
      color: #34495e;
      text-decoration: underline;
    }
  }
}

/* Education Section */
.education_item {
  margin-bottom: 1.5rem;
  border-left: 3px solid #42b883;
  padding-left: 1.5rem;
}

.school_info {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1rem;

  h3 {
    color: #42b883;
    font-size: 1.3rem;
    font-weight: 600;
  }

  .duration {
    color: #34495e;
    font-weight: 500;
  }
}

.edu_details {
  p {
    margin-bottom: 0.5rem;
  }
}

/* Career Goals Section */
.goals_container {
  display: flex;
  gap: 2rem;
  flex-wrap: wrap;
}

.goal_item {
  flex: 1;
  min-width: 300px;
  padding: 1.5rem;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);

  h3 {
    color: #42b883;
    margin-bottom: 1rem;
    font-size: 1.2rem;
    border-bottom: 2px solid #eaecef;
    padding-bottom: 0.5rem;
  }

  p {
    line-height: 1.6;
  }
}

.short_term {
  background-color: rgba(66, 184, 131, 0.1);
}

.long_term {
  background-color: rgba(52, 73, 94, 0.1);
}

/* Contact Section */
.contact_container {
  display: flex;
  flex-wrap: wrap;
  gap: 1.5rem;
}

.contact_item {
  flex: 1;
  min-width: 250px;
  display: flex;
  align-items: flex-start;
  gap: 1rem;
  padding: 1rem;
  border-radius: 8px;
  background-color: white;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
  transition:
    transform 0.3s,
    box-shadow 0.3s;

  &:hover {
    transform: translateY(-5px);
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }

  .icon {
    width: 40px;
    height: 40px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 50%;
    background-color: rgba(66, 184, 131, 0.1);

    img {
      width: 20px;
      height: 20px;
    }
  }

  .info {
    h3 {
      color: #2c3e50;
      font-size: 1.1rem;
      margin-bottom: 0.5rem;
    }

    a,
    p {
      color: #42b883;
      text-decoration: none;
      font-weight: 500;

      &:hover {
        text-decoration: underline;
      }
    }

    p {
      color: #34495e;
    }
  }
}

/* Responsive styles */
@media (max-width: 768px) {
  .goals_container {
    flex-direction: column;
  }

  .contact_container {
    flex-direction: column;
  }

  .company_info,
  .school_info {
    flex-direction: column;
    align-items: flex-start;

    .duration {
      margin-top: 0.5rem;
    }
  }
}
.block_skill {
  padding: 2rem;
  border-radius: 8px;
  background-color: #f8f9fa;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  max-width: 800px;
  margin: 0 auto;
}

.block_skill h2 {
  text-align: center;
  margin-bottom: 1.5rem;
  color: #2c3e50;
  font-size: 2rem;
}

.skill_category {
  margin-bottom: 2rem;
}

.skill_category h3 {
  color: #42b883; /* Vue.js green color */
  margin-bottom: 1rem;
  border-bottom: 2px solid #34495e;
  padding-bottom: 0.5rem;
  font-size: 1.5rem;
}

.skills_list {
  list-style: none;
  padding: 0;
}

.skills_list li {
  margin-bottom: 1rem;
}

.container-skill {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.container-skill .title {
  display: flex;
  align-items: center;
  gap: 1rem;
  & > div {
    flex: 1;
    display: flex;
    align-items: flex-end;
    justify-content: flex-end;
    span {
      font-weight: 600;
      color: #42b883;
    }
  }
}

.container-skill .title img {
  width: 30px;
  height: 30px;
  object-fit: contain;
}

.container-skill .title span {
  font-weight: 500;
  color: #2c3e50;
}

.progress-bar {
  height: 8px;
  width: 100%;
  background-color: #e9ecef;
  border-radius: 4px;
  overflow: hidden;
}

.progress-bar .progress {
  height: 100%;
  background: linear-gradient(90deg, #42b883, #35495e);
  border-radius: 4px;
  transition: width 1.5s ease-in-out;
}

@media (max-width: 768px) {
  .block_skill {
    padding: 1.5rem;
  }

  .block_skill h2 {
    font-size: 1.75rem;
  }

  .skill_category h3 {
    font-size: 1.25rem;
  }
}
.container_home {
  width: 90%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 100px 20px;

  .block_first {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 40px;
    .block_first_left {
      width: 50%;

      .text_1 {
        font-size: 18px;
        font-weight: bold;
      }
      .text_2 {
        font-size: 30px;
        font-weight: bold;
        color: var(--primary-color);
      }
      .text_3,
      .text_4 {
        font-size: 40px;
        font-weight: bold;
      }
      .text_4 {
        width: 70%;
        text-align: right;
        margin-bottom: 12px;
      }
      .block_description {
        margin-bottom: 12px;
      }
    }

    .block_first_right {
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;

      .block_thumb {
        border-radius: 100%;
        overflow: hidden;
      }
      .block_social_infor {
        display: flex;
        align-items: center;
        gap: 20px;
        margin-top: 12px;
        img {
          width: 24px;
          height: 24px;
        }
      }
    }
  }

  .block_project {
    margin-top: 100px;
    text-align: center;

    p {
      width: 50%;
      margin: 0 auto;
    }

    .cards {
      & > div {
        margin-bottom: 120px;
      }
      width: 100%;
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      margin-top: 70px;
    }
  }
}

/* --- Responsive --- */

/* Tablet */
@media (max-width: 1024px) {
  .container_home {
    width: 95%;
  }
  .block_first {
    flex-direction: column !important;
    text-align: center;

    .block_first_left,
    .block_first_right {
      width: 100%;
    }
  }

  .block_project p {
    width: 70% !important;
  }
}

/* Mobile */
@media (max-width: 768px) {
  .container_home {
    padding: 50px 0;
  }
  .container_home {
    width: 100% !important;
  }
  .block_first {
    flex-direction: column;
    gap: 20px;

    .block_first_left {
      text-align: center !important;
      width: 100% !important;
      .text_2 {
        font-size: 24px;
      }
      .text_3,
      .text_4 {
        font-size: 30px;
      }
      .text_4 {
        text-align: center;
      }
    }

    .block_first_right {
      .block_thumb img {
        width: 120px;
        height: 120px;
      }

      .block_social_infor {
        gap: 10px;
        img {
          width: 20px;
          height: 20px;
        }
      }
    }
  }

  .block_project p {
    width: 90% !important;
  }

  .cards {
    flex-direction: column !important;
    align-items: center;
  }
}
</style>
