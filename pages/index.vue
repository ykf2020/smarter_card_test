<template>
  <div class="container">
    <Card v-bind:event="event" v-for="event in data" :key="event.id" />
  </div>
</template>

<script>
import axios from "axios";
import Card from "~/components/Card.vue";
export default {
  components: {
    Card,
  },
  data() {
    return {
      data: [],
    };
  },
  methods: {
    fetch() {
      axios
        .get("https://event.smarter.com.tw/api/spa/bestseller/interview")
        .then((response) => {
          this.data = response.data.data.filter((el, index) => index > 0);
        });
    },
  },
  mounted() {
    this.fetch();
  },
};
</script>

<style>
.container {
  height: 100vh;
  width: 1029px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.card {
  position: relative;
  box-sizing: border-box;
  width: 323px;
  height: 388px;
  border-radius: 6px;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  align-items: center;
  box-shadow: 0 4px 4px rgba(112, 112, 112, 0.2);
}

.card__img {
  width: 100%;
  height: 177px;
  margin-bottom: 20px;
}

.card__img img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.card__info {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 0px 18px;
  height: calc(100% - 170px);
  overflow: hidden;
}

.card__info-title {
  font-size: 20px;
  margin-bottom: 20px;
}

.card__info-content {
  font-size: 16px;
}

.card__mask {
  position: absolute;
  bottom: 0;
  z-index: 9;
  width: 100%;
  height: 120px;
  background: linear-gradient(to top, white 65%, transparent);
}
.card__btn {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 108px;
  height: 40px;
  background-color: #404040;
  color: white;
  position: absolute;
  left: 50%;
  bottom: 18px;
  transform: translateX(-50%);
  border-radius: 4px;
  font-size: 14px;
  font-weight: bold;
}
</style>