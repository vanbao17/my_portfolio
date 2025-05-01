<template>
  <div class="card-item">
    <div class="card-thumb">
      <img :src="thumb" alt="Project Thumbnail" />
      <div class="overlay">
        <a :href="url" target="_blank" class="view-btn">View Project</a>
      </div>
    </div>
    <div class="card-content">
      <div class="card-header">
        <h3>{{ title }}</h3>
        <div class="position-badge">{{ posittion }}</div>
        <span class="status-indicator" :class="{ active: state }">
          {{ state ? "Active" : "Completed" }}
        </span>
      </div>
      <p class="description">{{ description }}</p>
      <div class="technologies" v-if="techs && techs.length">
        <h4>Technologies Used:</h4>
        <div class="tech-tags">
          <span v-for="(tech, index) in techs" :key="index" class="tech-tag">{{
            tech
          }}</span>
        </div>
      </div>
      <div class="project-links">
        <a :href="url" target="_blank" class="link-item">
          <img src="../assets/svg/link.svg" alt="Live Demo" />
          <span>Live Demo</span>
        </a>
        <a :href="github" target="_blank" class="link-item" v-if="github">
          <img src="../assets//icons/github.svg" alt="GitHub" />
          <span>Source Code</span>
        </a>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
defineProps({
  title: {
    type: String,
    required: true,
  },
  description: {
    type: String,
    required: true,
  },
  thumb: {
    type: String,
    required: true,
  },
  posittion: {
    type: String,
    required: true,
  },
  state: {
    type: Boolean,
    default: false,
  },
  url: {
    type: String,
    required: true,
  },
  github: {
    type: String,
    default: "",
  },
  techs: {
    type: Array as () => string[],
    default: () => [],
  },
});
</script>

<style scoped lang="scss">
.card-item {
  width: 100%;
  max-width: 380px;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
  transition:
    transform 0.3s ease,
    box-shadow 0.3s ease;
  margin: 0 15px 30px;
  background-color: #fff;

  &:hover {
    transform: translateY(-10px);
    box-shadow: 0 15px 30px rgba(0, 0, 0, 0.15);

    .card-thumb .overlay {
      opacity: 1;
    }
  }

  .card-thumb {
    height: 220px;
    position: relative;
    overflow: hidden;

    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.5s ease;
    }

    .overlay {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.7);
      display: flex;
      align-items: center;
      justify-content: center;
      opacity: 0;
      transition: opacity 0.3s ease;

      .view-btn {
        padding: 10px 20px;
        background-color: var(--primary-color, #42b883);
        color: white;
        border-radius: 30px;
        font-weight: 600;
        text-decoration: none;
        transition: all 0.3s ease;

        &:hover {
          background-color: white;
          color: var(--primary-color, #42b883);
        }
      }
    }
  }

  .card-content {
    padding: 20px;

    .card-header {
      position: relative;
      margin-bottom: 15px;

      h3 {
        font-size: 18px;
        font-weight: 700;
        color: #2c3e50;
        margin-bottom: 8px;
      }

      .position-badge {
        display: inline-block;
        padding: 4px 12px;
        background-color: rgba(66, 184, 131, 0.1);
        color: var(--primary-color, #42b883);
        font-size: 12px;
        font-weight: 600;
        border-radius: 20px;
        margin-bottom: 8px;
      }

      .status-indicator {
        position: absolute;
        top: 0;
        right: 0;
        font-size: 12px;
        font-weight: 600;
        color: #8c8c8c;

        &.active {
          color: #42b883;

          &:before {
            content: "";
            display: inline-block;
            width: 8px;
            height: 8px;
            border-radius: 50%;
            background-color: #42b883;
            margin-right: 5px;
          }
        }
      }
    }

    .description {
      color: #4a4a4a;
      font-size: 14px;
      line-height: 1.6;
      margin-bottom: 15px;
      height: 90px;
      overflow: hidden;
      text-overflow: ellipsis;
      display: -webkit-box;
      -webkit-line-clamp: 4;
      -webkit-box-orient: vertical;
    }

    .technologies {
      margin-bottom: 15px;

      h4 {
        font-size: 14px;
        font-weight: 600;
        color: #2c3e50;
        margin-bottom: 8px;
      }

      .tech-tags {
        display: flex;
        flex-wrap: wrap;
        gap: 8px;

        .tech-tag {
          padding: 4px 10px;
          background-color: #f0f0f0;
          border-radius: 15px;
          font-size: 12px;
          color: #4a4a4a;
        }
      }
    }

    .project-links {
      display: flex;
      gap: 15px;

      .link-item {
        display: flex;
        align-items: center;
        gap: 6px;
        text-decoration: none;
        color: #2c3e50;
        font-size: 14px;
        font-weight: 500;
        transition: color 0.3s ease;

        img {
          width: 16px;
          height: 16px;
        }

        &:hover {
          color: var(--primary-color, #42b883);
        }
      }
    }
  }
}

@media (max-width: 768px) {
  .card-item {
    max-width: 100%;
    margin: 0 0 30px;
  }
}
</style>
