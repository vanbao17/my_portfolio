<template>
  <div class="card-item" :class="{ featured: isFeatured }">
    <!-- Badge góc trên -->
    <div v-if="isFeatured" class="featured-badge">
      <svg width="12" height="12" viewBox="0 0 24 24" fill="currentColor">
        <path
          d="12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"
        />
      </svg>
      Featured
    </div>

    <div class="card-thumb">
      <div class="image-container">
        <img :src="thumb" :alt="title + ' thumbnail'" loading="lazy" />
        <div class="image-gradient"></div>
      </div>

      <div class="overlay">
        <div class="overlay-content">
          <a
            :href="url"
            target="_blank"
            rel="noopener noreferrer"
            class="view-btn"
          >
            <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor">
              <path
                d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"
              />
            </svg>
            View Project
          </a>
          <a
            v-if="github"
            :href="github"
            target="_blank"
            rel="noopener noreferrer"
            class="github-btn"
          >
            <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor">
              <path
                d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"
              />
            </svg>
            Source
          </a>
        </div>
      </div>

      <!-- Status indicator trên ảnh -->
      <div class="status-pill" :class="{ active: state }">
        <div class="status-dot"></div>
        {{ state ? "Active" : "Completed" }}
      </div>
    </div>

    <div class="card-content">
      <div class="card-header">
        <div class="title-section">
          <h3>{{ title }}</h3>
          <div class="position-badge">
            <svg width="12" height="12" viewBox="0 0 24 24" fill="currentColor">
              <path
                d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"
              />
            </svg>
            {{ posittion }}
          </div>
        </div>
      </div>

      <p class="description">{{ description }}</p>

      <div class="technologies" v-if="techs && techs.length">
        <h4>
          <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor">
            <path
              d="M9.4 16.6L4.8 12l4.6-4.6L8 6l-6 6 6 6 1.4-1.4zm5.2 0L19.2 12l-4.6-4.6L16 6l6 6-6 6-1.4-1.4z"
            />
          </svg>
          Technologies
        </h4>
        <div class="tech-tags">
          <span
            v-for="(tech, index) in techs"
            :key="index"
            class="tech-tag"
            :style="{ animationDelay: `${index * 0.1}s` }"
          >
            {{ tech }}
          </span>
        </div>
      </div>

      <div class="card-footer">
        <div class="project-links">
          <a
            :href="url"
            target="_blank"
            rel="noopener noreferrer"
            class="link-item primary"
          >
            <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor">
              <path
                d="M19 19H5V5h7V3H5c-1.11 0-2 .9-2 2v14c0 1.1.89 2 2 2h14c1.11 0 2-.9 2-2v-7h-2v7zM14 3v2h3.59l-9.83 9.83 1.41 1.41L19 6.41V10h2V3h-7z"
              />
            </svg>
            Live Demo
          </a>
          <a
            v-if="github"
            :href="github"
            target="_blank"
            rel="noopener noreferrer"
            class="link-item secondary"
          >
            <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor">
              <path
                d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"
              />
            </svg>
            GitHub
          </a>
        </div>

        <div class="interaction-buttons">
          <button
            @click="toggleLike"
            class="like-btn"
            :class="{ liked: isLiked }"
          >
            <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor">
              <path
                d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"
              />
            </svg>
            {{ likeCount }}
          </button>
          <button
            @click="toggleBookmark"
            class="bookmark-btn"
            :class="{ bookmarked: isBookmarked }"
          >
            <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor">
              <path d="M17 3H7c-1.1 0-2 .9-2 2v16l7-3 7 3V5c0-1.1-.9-2-2-2z" />
            </svg>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from "vue";

interface Props {
  title: string;
  description: string;
  thumb: string;
  posittion: string;
  state?: boolean;
  url: string;
  github?: string;
  techs?: string[];
  isFeatured?: boolean;
  initialLikes?: number;
}

const props = withDefaults(defineProps<Props>(), {
  state: false,
  github: "",
  techs: () => [],
  isFeatured: false,
  initialLikes: 0,
});

// Reactive states
const isLiked = ref(false);
const isBookmarked = ref(false);
const likeCount = ref(props.initialLikes);

// Methods
const toggleLike = () => {
  isLiked.value = !isLiked.value;
  likeCount.value += isLiked.value ? 1 : -1;
};

const toggleBookmark = () => {
  isBookmarked.value = !isBookmarked.value;
};

// Computed
const truncatedDescription = computed(() => {
  return props.description.length > 150
    ? props.description.substring(0, 150) + "..."
    : props.description;
});
</script>

<style scoped lang="scss">
.card-item {
  width: 100%;
  max-width: 400px;
  border-radius: 20px;
  overflow: hidden;
  background: linear-gradient(145deg, #ffffff 0%, #f8fafc 100%);
  box-shadow:
    0 10px 25px rgba(0, 0, 0, 0.08),
    0 4px 12px rgba(0, 0, 0, 0.05),
    0 0 0 1px rgba(255, 255, 255, 0.8);
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  margin: 0 15px 30px;
  position: relative;
  backdrop-filter: blur(10px);

  &.featured {
    border: 2px solid transparent;
    background: linear-gradient(145deg, #ffffff 0%, #f0f9ff 100%);

    &::before {
      content: "";
      position: absolute;
      inset: 0;
      border-radius: 20px;
      padding: 2px;
      background: linear-gradient(135deg, #3b82f6, #8b5cf6, #ec4899);
      mask:
        linear-gradient(#fff 0 0) content-box,
        linear-gradient(#fff 0 0);
      mask-composite: exclude;
      z-index: -1;
    }
  }

  &:hover {
    transform: translateY(-12px) scale(1.02);
    box-shadow:
      0 25px 50px rgba(0, 0, 0, 0.15),
      0 10px 30px rgba(0, 0, 0, 0.1),
      0 0 0 1px rgba(255, 255, 255, 0.9);

    .card-thumb {
      .image-container img {
        transform: scale(1.1);
      }

      .overlay {
        opacity: 1;
        backdrop-filter: blur(8px);
      }
    }

    .tech-tag {
      transform: translateY(-2px);
    }
  }

  .featured-badge {
    position: absolute;
    top: 15px;
    right: 15px;
    background: linear-gradient(135deg, #fbbf24, #f59e0b);
    color: white;
    padding: 6px 12px;
    border-radius: 20px;
    font-size: 11px;
    font-weight: 600;
    z-index: 10;
    display: flex;
    align-items: center;
    gap: 4px;
    box-shadow: 0 4px 12px rgba(251, 191, 36, 0.3);
    animation: pulse 2s infinite;

    @keyframes pulse {
      0%,
      100% {
        transform: scale(1);
      }
      50% {
        transform: scale(1.05);
      }
    }
  }

  .card-thumb {
    height: 240px;
    position: relative;
    overflow: hidden;

    .image-container {
      position: relative;
      width: 100%;
      height: 100%;

      img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        transition: transform 0.6s cubic-bezier(0.4, 0, 0.2, 1);
      }

      .image-gradient {
        position: absolute;
        bottom: 0;
        left: 0;
        right: 0;
        height: 40%;
        background: linear-gradient(to top, rgba(0, 0, 0, 0.3), transparent);
      }
    }

    .status-pill {
      position: absolute;
      top: 15px;
      left: 15px;
      background: rgba(255, 255, 255, 0.95);
      backdrop-filter: blur(10px);
      color: #64748b;
      padding: 6px 12px;
      border-radius: 20px;
      font-size: 12px;
      font-weight: 600;
      display: flex;
      align-items: center;
      gap: 6px;
      z-index: 5;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);

      .status-dot {
        width: 8px;
        height: 8px;
        border-radius: 50%;
        background-color: #ef4444;
        animation: pulse 2s infinite;
      }

      &.active {
        color: #059669;

        .status-dot {
          background-color: #10b981;
        }
      }
    }

    .overlay {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.6);
      display: flex;
      align-items: center;
      justify-content: center;
      opacity: 0;
      transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);

      .overlay-content {
        display: flex;
        gap: 12px;
        flex-direction: column;
        align-items: center;

        a {
          display: flex;
          align-items: center;
          gap: 8px;
          padding: 12px 24px;
          border-radius: 30px;
          font-weight: 600;
          text-decoration: none;
          transition: all 0.3s ease;
          backdrop-filter: blur(10px);
          border: 1px solid rgba(255, 255, 255, 0.2);

          &.view-btn {
            background: linear-gradient(135deg, #3b82f6, #1d4ed8);
            color: white;
            box-shadow: 0 8px 20px rgba(59, 130, 246, 0.3);

            &:hover {
              background: linear-gradient(135deg, #1d4ed8, #1e40af);
              transform: translateY(-2px);
              box-shadow: 0 12px 30px rgba(59, 130, 246, 0.4);
            }
          }

          &.github-btn {
            background: rgba(255, 255, 255, 0.9);
            color: #1f2937;

            &:hover {
              background: white;
              transform: translateY(-2px);
              box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
            }
          }
        }
      }
    }
  }

  .card-content {
    padding: 24px;

    .card-header {
      margin-bottom: 16px;

      .title-section {
        h3 {
          font-size: 20px;
          font-weight: 700;
          color: #1f2937;
          margin-bottom: 10px;
          line-height: 1.3;
        }

        .position-badge {
          display: inline-flex;
          align-items: center;
          gap: 6px;
          padding: 6px 14px;
          background: linear-gradient(
            135deg,
            rgba(59, 130, 246, 0.1),
            rgba(147, 51, 234, 0.1)
          );
          color: #3b82f6;
          font-size: 13px;
          font-weight: 600;
          border-radius: 20px;
          border: 1px solid rgba(59, 130, 246, 0.2);
        }
      }
    }

    .description {
      color: #64748b;
      font-size: 14px;
      line-height: 1.6;
      margin-bottom: 20px;
      height: auto;
    }

    .technologies {
      margin-bottom: 20px;

      h4 {
        font-size: 14px;
        font-weight: 600;
        color: #374151;
        margin-bottom: 10px;
        display: flex;
        align-items: center;
        gap: 6px;
      }

      .tech-tags {
        display: flex;
        flex-wrap: wrap;
        gap: 8px;

        .tech-tag {
          padding: 6px 12px;
          background: linear-gradient(135deg, #f1f5f9, #e2e8f0);
          border: 1px solid #e2e8f0;
          border-radius: 16px;
          font-size: 12px;
          font-weight: 500;
          color: #475569;
          transition: all 0.3s ease;
          animation: slideInUp 0.5s ease both;

          &:hover {
            background: linear-gradient(135deg, #ddd6fe, #c4b5fd);
            color: #7c3aed;
            border-color: #c4b5fd;
            transform: translateY(-1px);
          }

          @keyframes slideInUp {
            from {
              opacity: 0;
              transform: translateY(10px);
            }
            to {
              opacity: 1;
              transform: translateY(0);
            }
          }
        }
      }
    }

    .card-footer {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-top: 20px;
      padding-top: 20px;
      border-top: 1px solid #e5e7eb;

      .project-links {
        display: flex;
        gap: 12px;

        .link-item {
          display: flex;
          align-items: center;
          gap: 6px;
          padding: 8px 16px;
          border-radius: 20px;
          text-decoration: none;
          font-size: 13px;
          font-weight: 500;
          transition: all 0.3s ease;
          border: 1px solid transparent;

          &.primary {
            background: linear-gradient(135deg, #3b82f6, #1d4ed8);
            color: white;
            box-shadow: 0 4px 12px rgba(59, 130, 246, 0.2);

            &:hover {
              transform: translateY(-1px);
              box-shadow: 0 6px 16px rgba(59, 130, 246, 0.3);
            }
          }

          &.secondary {
            background: rgba(107, 114, 128, 0.1);
            color: #6b7280;
            border-color: #e5e7eb;

            &:hover {
              background: rgba(107, 114, 128, 0.2);
              color: #374151;
              transform: translateY(-1px);
            }
          }
        }
      }

      .interaction-buttons {
        display: flex;
        gap: 8px;

        button {
          display: flex;
          align-items: center;
          gap: 4px;
          padding: 8px 12px;
          border: none;
          border-radius: 16px;
          background: rgba(107, 114, 128, 0.1);
          color: #6b7280;
          font-size: 12px;
          font-weight: 500;
          cursor: pointer;
          transition: all 0.3s ease;

          &:hover {
            background: rgba(107, 114, 128, 0.2);
            transform: scale(1.05);
          }

          &.liked {
            background: linear-gradient(135deg, #fecaca, #fee2e2);
            color: #dc2626;
          }

          &.bookmarked {
            background: linear-gradient(135deg, #ddd6fe, #e0e7ff);
            color: #7c3aed;
          }
        }
      }
    }
  }
}

@media (max-width: 768px) {
  .card-item {
    max-width: 100%;
    margin: 0 0 24px;
    border-radius: 16px;

    .card-content {
      padding: 20px;
    }

    .card-footer {
      flex-direction: column;
      gap: 16px;
      align-items: stretch;

      .project-links {
        justify-content: center;
      }

      .interaction-buttons {
        justify-content: center;
      }
    }
  }
}
</style>
