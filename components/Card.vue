<template>
  <div class="card">
    <div class="card__img">
      <img
        :src="event.previewPictureSrc"
      />
    </div>
    <div class="card__info">
      <h1 class="card__info-title">{{event.title}}</h1>
      <p class="card__info-content">
        {{ event.previewContext }}
      </p>
    </div>
    <div class="card__mask">
      <a class="card__btn" :href="event.url">立即前往 &#62</a>
    </div>
  </div>
</template>


<script>
export default {
  props: {
    event: Object,
  },
};
</script>