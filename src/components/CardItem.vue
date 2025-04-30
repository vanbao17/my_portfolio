<script setup lang="ts">
import Button from "./common/Button.vue";
const props = defineProps<{
  title: string;
  thumb: string;
  description: string;
  posittion: string;
  state: boolean;
  url: string;
}>();
const handleUrl = () => {
  window.open(props.url, "_blank");
};
</script>
<template>
  <div class="wrapper_card">
    <div class="container_card">
      <img v-if="state === true" :src="props.thumb" :alt="props.title" />
      <div class="card">
        <p class="title">{{ props.title }}</p>
        <span>{{ props.posittion }}</span>
        <p class="desc">{{ props.description }}</p>
        <div class="button" @click="handleUrl">
          <Button type="primary" title="Xem demo"></Button>
        </div>
      </div>
      <img v-if="state === false" :src="props.thumb" :alt="props.title" />
    </div>
  </div>
</template>
<style scoped lang="scss">
.wrapper_card {
  width: 100%;
  .container_card {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 20px;

    img {
      width: 40%;
      object-fit: cover;
      border-radius: 8px;
    }

    .card {
      width: 50%;
      display: flex;
      flex-direction: column;
      gap: 10px;

      .title {
        font-size: 20px;
        font-weight: 700;
      }

      span {
        color: var(--primary-color);
        font-weight: 500;
      }

      .desc {
        font-size: 14px;
        color: #555;
        line-height: 1.6;
      }

      .button {
        width: 100%;
        display: flex;
        align-items: flex-end;
        justify-content: flex-end;
        margin-top: 12px;
      }
    }
  }
}

/* --- Responsive --- */

/* Tablet */
@media (max-width: 1024px) {
  .container_card {
    flex-direction: column;
    text-align: center;
    gap: 30px;

    img {
      width: 60% !important;
    }

    .card {
      width: 80% !important;
      .button {
        justify-content: center;
        display: flex;
        align-items: center;
      }
    }
  }
}

/* Mobile */
@media (max-width: 768px) {
  .container_card {
    width: 100% !important;
    flex-direction: column;
    align-items: center;
    text-align: center;
    gap: 20px;

    img {
      width: 100% !important;
      max-width: 300px;
    }

    .card {
      width: 100% !important;
      // padding: 0 15px;
      .title {
        font-size: 18px;
      }

      .desc {
        font-size: 14px;
      }

      .button {
        justify-content: center !important;
        display: flex;
        align-items: center !important;
      }
    }
  }
}
</style>
