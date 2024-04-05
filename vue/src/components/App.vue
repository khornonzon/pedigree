<template>
  <div
    @mousemove="() => resetTimer()"
    @keypress="() => resetTimer()"
  >
    <RouterView v-if="isActive" />
    <ScreenSaver v-else />
    <GalleryPage :images="images"/>
    <ModalContainer />
  </div>
</template>

<script>
import ModalContainer from "@/components/parts/ModalContainer"
import ScreenSaver from "@/components/modals/ScreenSaver.vue"
import GalleryPage from "./pages/GalleryPage.vue";

export default {
  components: {
    ModalContainer,
    ScreenSaver,
    GalleryPage
  },
  data () {
    return {
      isActive: true,
      timer: null,
      images: [
        {
          id: 1,
          img: 'https://digital.ihg.com/is/image/ihg/kimpton-amsterdam-7775502464-2x1',
          title: 'Заголовок 1',
          description: 'Описание 1'
        },
        {
          id: 2,
          img: 'https://mykaleidoscope.ru/x/uploads/posts/2022-09/1663091191_10-mykaleidoscope-ru-p-gollandiya-vkontakte-12.jpg',
          title: 'Заголовок 2',
          description: 'Описание 2'
        },
        {
          id: 3,
          img: 'https://mykaleidoscope.ru/x/uploads/posts/2022-09/1663116593_15-mykaleidoscope-ru-p-stolitsa-gollandii-dostoprimechatelnosti-16.jpg',
          title: 'Заголовок 3',
          description: 'Описание 3'
        },
        {
          id: 4,
          img: 'https://mykaleidoscope.ru/x/uploads/posts/2022-09/1663116505_5-mykaleidoscope-ru-p-stolitsa-gollandii-dostoprimechatelnosti-6.jpg',
          title: 'Заголовок 4',
          description: 'Описание 4'
        },
        {
          id: 5,
          img: 'https://mobimg.b-cdn.net/v3/fetch/35/35396356823d083b4d7120941364cd99.jpeg',
          title: 'Заголовок 5',
          description: 'Описание 5'
        },
        {
          id: 10,
          img: 'https://digital.ihg.com/is/image/ihg/kimpton-amsterdam-7775502464-2x1',
          title: 'Заголовок 1',
          description: 'Описание 1'
        },
        {
          id: 20,
          img: 'https://mykaleidoscope.ru/x/uploads/posts/2022-09/1663091191_10-mykaleidoscope-ru-p-gollandiya-vkontakte-12.jpg',
          title: 'Заголовок 2',
          description: 'Описание 2'
        },
        {
          id: 30,
          img: 'https://mykaleidoscope.ru/x/uploads/posts/2022-09/1663116593_15-mykaleidoscope-ru-p-stolitsa-gollandii-dostoprimechatelnosti-16.jpg',
          title: 'Заголовок 3',
          description: 'Описание 3'
        },
        {
          id: 40,
          img: 'https://mykaleidoscope.ru/x/uploads/posts/2022-09/1663116505_5-mykaleidoscope-ru-p-stolitsa-gollandii-dostoprimechatelnosti-6.jpg',
          title: 'Заголовок 4',
          description: 'Описание 4'
        },
        {
          id: 50,
          img: 'https://mobimg.b-cdn.net/v3/fetch/35/35396356823d083b4d7120941364cd99.jpeg',
          title: 'Заголовок 5',
          description: 'Описание 5'
        }
      ]
    }
  },
  mounted() {
    this.resetTimer();
  },
  methods: {
    resetTimer() {
      this.isActive = true
      if (this.timer) {
        clearTimeout(this.timer)
      }
      this.timer = setTimeout(() => {
        this.isActive = false;
      }, 5 * 60 * 1000)
    },
  },
}
</script>

<style lang="less">
@import url('https://fonts.googleapis.com/css2?family=Jost:wght@400;700&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');

body {
  margin: 0;
  padding: 0;
  background-color: @cBaseTwo;
  font-family: @ffInter;
  overflow-y: scroll;
}

a {
  text-decoration: none;
}

section {
  background-color: @cBaseOne;
  margin-bottom: 20px;
  border-radius: 2px;
  box-sizing: border-box;

  &:last-child {
    margin-bottom: 0;
  }
}

h1, h2, h3, h4, h5 {
  font-family: @ffInter;
  color: @cBaseThree;
  margin: 0;
  margin-bottom: 8px;
}

h1 {
  font-size: 26px;
}

h2 {
  font-size: 20px;
}

h3 {
  font-size: 18px;
}

h4 {
  font-size: 16px;
}

.p-16 {
  padding: 16px;
}

.d-flex {
  display: flex;
}

.custom-form {
  width: 450px;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 15px;
  margin-bottom: 15px;

  @media (max-width: 720px) {
    display: flex;
    width: 100%;
    flex-direction: column;
  }

  &__full-width {
    grid-column: span 2
  }

  &__input {

    &.el-date-editor {
      width: 100% !important;
    }

    & .el-input__inner {
      font-size: 14px;
      width: 100%;
      font-family: @ffInter;
    }

    & .el-textarea__inner {
      font-size: 14px;
      width: 100%;
      font-family: @ffInter;
      min-height: 100px !important;
    }
  }
}

.custom-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 15px;
}
</style>
