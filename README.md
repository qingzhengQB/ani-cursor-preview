# ani-cursor-preview

网页由 vue 编写，仅有一个 App.vue 文件

```vue
<template>
  <h2>Ani-cursor.js Preview 效果预览</h2>
  <div class="version-tip">
    过低的浏览器版本可能会导致动态指针失效 / Low browser version may cause
    dynamic mouse pointer failure
  </div>
  <div class="preview-container">
    <div class="preview-aria1 preview-aria">Help</div>
    <div class="preview-aria2 preview-aria">Busy</div>
    <div class="preview-aria3 preview-aria">Working</div>
    <div class="preview-aria text-aria">
      <p>Text Area. Move mouse on the text to see the effect.</p>
      <span>Text Area. Move mouse on the text to see the effect.</span>
      <p>Text Area. Move mouse on the text to see the effect.</p>
      <span>Text Area. Move mouse on the text to see the effect.</span>
      <textarea rows="4" type="text" :placeholder="textAriaTips" />
    </div>
  </div>
  <tip
    >预览 ani 文件来源于B站UP
    Moos柚眠：【【初音未来】鼠标指针，来喽！-哔哩哔哩】
    https://b23.tv/VsVhfiU</tip
  >
</template>

<script setup>
import { onMounted } from "vue";
import { setANICursor, setANICursorWithGroupElement } from "ani-cursor.js";
setANICursor("body", "/ani-cursor-preview/ani/Main.ani");
setANICursor(".preview-aria1", "/ani-cursor-preview/ani/Help.ani");
setANICursor(".preview-aria2", "/ani-cursor-preview/ani/Busy.ani");
setANICursor(".preview-aria3", "/ani-cursor-preview/ani/Work.ani");
let textAbleGroup = [
  "input",
  'input[type="text"]',
  "textarea",
  "span",
  "p",
  "h1",
  "h2",
  "h3",
  "h4",
  "h5",
  "h6",
];
setANICursorWithGroupElement(
  textAbleGroup,
  "/ani-cursor-preview/ani/TextSelect.ani"
);
const textAriaTips = `Text Area. Move mouse on the text to see the effect.
Code on this textarea: 
let textAbleGroup = ["input",'input[type="text"]', "textarea", "span", "p", "h1", "h2", "h3", "h4", "h5", "h6"];
setANICursorWithGroupElement(textAbleGroup, "/ani-cursor-preview/ani/TextSelect.ani");
`;
</script>

<style lang="scss">
body {
  margin: 0;
  background-color: #f0f0f0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 10px;
}
.preview-container {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
  gap: 30px;
  margin: 15px 0;
}
.preview-aria {
  width: 1000px;
  height: 120px;
  background-color: bisque;
  border-radius: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 1.5rem;
  font-weight: bolder;
}
.text-aria {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: auto;
  font-weight: normal;
  & textarea {
    width: 60%;
    height: 150px;
    margin: 20px 0;
  }
}
</style>
```
