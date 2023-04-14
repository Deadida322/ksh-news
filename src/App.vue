<template>
  <v-app>
    <v-main>
      <v-container>
        <v-row no-gutters>
          <v-col cols="2"></v-col>
          <v-col cols="8">
            <v-text-field v-model="query" hint="Поиск по новостям" solo label="Найти новость"
              append-icon="mdi-magnify"></v-text-field>
            <div v-if="computedNews.length" class="d-flex justify-space-between flex-wrap">
              <NewsItem class="mb-4 w-50" v-for="item in computedNews" :news="item"></NewsItem>
            </div>
            <v-alert v-else text prominent type="error" icon="mdi-cloud-alert">
              Новостей по данному запросу не обнаружено
            </v-alert>
            <div class="d-flex">
              <v-spacer></v-spacer>
              <template v-if="!query">
                <v-btn v-if="news.length >= toShow" @click="toShow += 4" color="primary">
                  Ещё новости
                </v-btn>
                <v-btn v-else @click="toShow = 4">
                  Скрыть
                </v-btn>
              </template>
              <v-spacer></v-spacer>
            </div>
          </v-col>
          <v-col cols="2"></v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import NewsItem from './components/NewsItem.vue';
export default {
  name: 'App',

  components: {
    NewsItem
  },

  data: () => ({
    toShow: 4,
    query: "",
    news: [
      {
        title: "Мама мыла раму",
        img: "https://proprikol.ru/wp-content/uploads/2020/08/kartinki-lamy-13.jpg",
        description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Fugiat labore nesciunt libero dolores dolor hic nobis soluta a beatae obcaecati adipisci recusandae voluptates, possimus harum officiis sed consequatur quo mollitia?",
        date: "12-02-2023",
        tags: ['tag1', 'мама', 'рама', 'tag2']
      },
      {
        title: "А Карл украл кларнет",
        img: "https://static.cdn.asset.aparat.com/avt/27720778-7133-b__4209.jpg",
        description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Fugiat labore nesciunt libero dolores dolor hic nobis soluta a beatae obcaecati adipisci recusandae voluptates, possimus harum officiis sed consequatur quo mollitia?",
        date: "12-04-2022",
        tags: ['рама', 'tag2']
      },
      {
        title: "Клара коралловна",
        img: "https://avatars.dzeninfra.ru/get-zen_doc/1592767/pub_62a3799c607c09351143dce9_62a8ca3e51bab32d0f081dc8/scale_1200",
        description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Fugiat labore nesciunt libero dolores dolor hic nobis soluta a beatae obcaecati adipisci recusandae voluptates, possimus harum officiis sed consequatur quo mollitia?",
        date: "12-04-2022",
        tags: ['рама', 'tag2']
      },
      {
        title: "Мама мыла раму",
        img: "https://proprikol.ru/wp-content/uploads/2020/08/kartinki-lamy-13.jpg",
        description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Fugiat labore nesciunt libero dolores dolor hic nobis soluta a beatae obcaecati adipisci recusandae voluptates, possimus harum officiis sed consequatur quo mollitia?",
        date: "12-02-2023",
        tags: ['tag1', 'мама', 'рама', 'tag2']
      },
      {
        title: "А Карл украл кларнет",
        img: "https://static.cdn.asset.aparat.com/avt/27720778-7133-b__4209.jpg",
        description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Fugiat labore nesciunt libero dolores dolor hic nobis soluta a beatae obcaecati adipisci recusandae voluptates, possimus harum officiis sed consequatur quo mollitia?",
        date: "12-04-2022",
        tags: ['рама', 'tag2']
      },
      {
        title: "Клара коралловна",
        img: "https://avatars.dzeninfra.ru/get-zen_doc/1592767/pub_62a3799c607c09351143dce9_62a8ca3e51bab32d0f081dc8/scale_1200",
        description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Fugiat labore nesciunt libero dolores dolor hic nobis soluta a beatae obcaecati adipisci recusandae voluptates, possimus harum officiis sed consequatur quo mollitia?",
        date: "12-04-2022",
        tags: ['рама', 'tag2']
      },
      {
        title: "Мама мыла раму",
        img: "https://proprikol.ru/wp-content/uploads/2020/08/kartinki-lamy-13.jpg",
        description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Fugiat labore nesciunt libero dolores dolor hic nobis soluta a beatae obcaecati adipisci recusandae voluptates, possimus harum officiis sed consequatur quo mollitia?",
        date: "12-02-2023",
        tags: ['tag1', 'мама', 'рама', 'tag2']
      },
      {
        title: "А Карл украл кларнет",
        img: "https://static.cdn.asset.aparat.com/avt/27720778-7133-b__4209.jpg",
        description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Fugiat labore nesciunt libero dolores dolor hic nobis soluta a beatae obcaecati adipisci recusandae voluptates, possimus harum officiis sed consequatur quo mollitia?",
        date: "12-04-2022",
        tags: ['рама', 'tag2']
      },
      {
        title: "Клара коралловна",
        img: "https://avatars.dzeninfra.ru/get-zen_doc/1592767/pub_62a3799c607c09351143dce9_62a8ca3e51bab32d0f081dc8/scale_1200",
        description: "Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing Lorem ipsum dolor sit amet consectetur adipisicing elit. Fugiat labore nesciunt libero dolores dolor hic nobis soluta a beatae obcaecati adipisci recusandae voluptates, possimus harum officiis sed consequatur quo mollitia?",
        date: "12-04-2022",
        tags: ['рама', 'tag2']
      },
    ]
  }),
  computed: {
    computedNews() {
      if (this.query) {
        return this.news.filter(item => {
          if (item.title.toLowerCase().indexOf(this.query.toLowerCase()) !== -1) {
            return true
          }
        })
      }
      return this.news.slice(0, this.toShow)
    }
  }
};
</script>

<style>
.w-50 {
  width: 49.5%;
}
</style>
