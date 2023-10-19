/
<template>
  <div>
    <div class="title">文章</div>
    <div v-for="article in articles" :key="article.id" class="article">
      <h3>{{ article.title }}</h3>
      <div class="flex">
        <div class="article__container">
          <div class="container__user">
            <img :src="article.userAvatar" alt="avatar" class="user__avatar" />
            <p>{{ article.userName }}</p>
            <p>{{ article.date }}</p>
          </div>
          <!-- <div class="container__content">{{ article.content }}</div> -->
          <div class="container__content" v-if="article.img.length === 1">
            {{ article.content }}
          </div>
          <div class="container__content2" v-else>
            {{ article.content }}
          </div>
        </div>
        <!-- <img :src="article.img" class="article__img" /> -->
        <div class="article__img-container">
          <img
            v-for="(imgPath, index) in article.img"
            :key="index"
            :src="imgPath"
            class="article__img"
          />
        </div>
      </div>
      <div class="article__footer">
        <span v-for="tag in article.tag" :key="tag" class="footer__tag">
          <p>{{ tag }}</p>
        </span>
        <div
          v-for="(like, key) in article.likeList"
          :key="key"
          class="footer__likeList"
        >
          <p>{{ key }}：{{ like }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      articles: [
        {
          id: 1,
          title: `我好像有什麼事情很悲哀，我想起"生命"`,
          userAvatar: require("../assets/images/test.jpg"),
          userName: "張杰攻",
          date: "2021.09.12",
          content:
            "有什麼人能用綠竹作弓矢，射入雲空，永不落下？我之想像，猶如長箭，向雲而去",
          img: [require("../assets/images/test.jpg")],
          tag: ["美文", "故事", "精選優質"],
          likeList: {
            like: 231,
            collect: 11,
            comment: 34,
            views: 786,
          },
        },
        {
          id: 2,
          title: `我好像有什麼事情很悲哀，我想起"生命"`,
          userAvatar: require("../assets/images/test.jpg"),
          userName: "張杰攻",
          date: "2021.09.12",
          content: "一群客人擠在客廳裡，誰也不肯先做，誰也不肯首座",
          img: [
            require("../assets/images/test.jpg"),
            require("../assets/images/test.jpg"),
            require("../assets/images/test.jpg"),
          ],
          tag: ["美文", "故事", "精選優質"],
          likeList: {
            like: 231,
            collect: 11,
            comment: 34,
            views: 786,
          },
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
.title {
  width: 100%;
  height: 10vw;
  background-color: black;
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
}
h3 {
  display: flex;
}

.article {
  display: flex;
  flex-direction: column;
  padding: 16px;
  background-color: #d7e9f4;
  margin-bottom: 16px;
}

.flex {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  // height: 15vh;
}

.article__container {
  .container__user {
    display: flex;
    align-items: center;

    .user__avatar {
      border-radius: 100%;
      height: 5vh;
      width: 5vh;
      margin-right: 2vw;
    }

    p {
      margin-left: 1vw;
    }
  }

  .container__content {
    width: 60vw;
    height: 3em;
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-line-clamp: 2;
    overflow: hidden;
  }
  .container__content2 {
    width: 90vw;
    height: 3em;
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
  }
}

.article__img {
  width: 25vw;
  height: 20vw;
  border-radius: 5px;
  margin-right: 8px;
}

.article__footer {
  display: flex;
  // flex-direction: column;

  .footer__tag {
    background-color: #3498db;
    color: #ffffff;
    padding: 2px 2px;
    border-radius: 4px;
    margin-right: 4px;
    font-size: 12px;
    display: inline-block;
    line-height: 14px;
  }
  .footer__likeList {
    font-size: 12px;
    // margin: ;
  }
}
</style>
