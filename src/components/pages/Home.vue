<script setup lang="ts">
import Button from "../common/Button.vue";
import CardItem from "../CardItem.vue";
import "animate.css";
import { ref, onMounted } from "vue";
const animatedDiv1 = ref(HTMLDivElement | null);
const animatedDiv2 = ref(HTMLDivElement | null);
const animatedDiv3 = ref(HTMLDivElement | null);
const animatedDiv4 = ref(HTMLDivElement | null);
const animatedDiv5 = ref(HTMLDivElement | null);
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
      <div class="block_skill" id="block_skill" ref="animatedDiv5">
        <h2>Kỹ năng</h2>
        <div class="skill_category">
          <h3>🎨 Front-end</h3>
          <ul class="skills_list">
            <li>
              <div class=""></div>
            </li>
            <li>React.js</li>
            <li>Vue.js</li>
            <li>TypeScript</li>
          </ul>
        </div>

        <div class="skill_category">
          <h3>🧱 Back-end</h3>
          <ul class="skills_list">
            <li>Node.js, RESTful API</li>
            <li>MySQL, SQL Server</li>
          </ul>
        </div>

        <div class="skill_category">
          <h3>⚙️ DevOps & Khác</h3>
          <ul class="skills_list">
            <li>Docker, VPS, Git, GitHub</li>
            <li>AI cơ bản (Python, nhận diện ảnh nhạy cảm)</li>
          </ul>
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
              thumb="https://res.cloudinary.com/dumeexund/image/upload/v1744555820/project/evuzrkkq6nneupfnau9v.png"
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
              title="LifeLink Social Website"
              posittion="Fullstack Developer"
              :state="true"
              url="https://senvb-trangban.vercel.app/"
            ></CardItem>
          </div>
        </div>
        <div></div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.wrapper_home {
  width: 100%;
}

.block_skill {
  .skill_category {
    display: flex;
    flex-direction: column;
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
