<template>
  <div class="app-background">
    <div class="button-container">
      <button class="post-note-button" @click="postNote">シャミ子が悪いんだよ</button>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  methods: {
    async postNote() {
      const apiUrl = process.env.VUE_APP_MISSKEY_API_URL;
      const apiToken = process.env.VUE_APP_MISSKEY_API_TOKEN;
      const text = 'シャミ子が悪いんだよ';

      try {
        await axios.post(apiUrl, {
          i: apiToken,
          text: text,
        });
        alert('ノートが投稿されました！');
      } catch (error) {
        console.error(error);
        alert('ノートの投稿に失敗しました。');
      }
    },
  },
};
</script>

<style scoped>
.app-background {
  background-color: #f0e5f2; /* ページ全体の背景色 */
  height: 100vh;
  width: 100%;
}

.button-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}

.post-note-button {
  background-color: #ff69b4; /* シャミ子のイメージカラー */
  border: none;
  border-radius: 50px;
  color: white;
  cursor: pointer;
  font-size: 1.2rem;
  padding: 15px 30px;
  text-align: center;
  text-decoration: none;
  transition: background-color 0.3s;
}

.post-note-button:hover {
  background-color: #ff8ac0;
}

body {
  margin: 0px;
}
</style>