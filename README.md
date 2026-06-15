# ani-cursor-preview

网页由 vue 编写，仅有一个 App.vue 文件

```vue
<template>
  <div class="hero">
    <h1>ani-cursor.js</h1>
    <div class="version-tip">
      过低的浏览器版本可能会导致动态指针失效 / Low browser version may cause
      dynamic mouse pointer failure
    </div>
  </div>

  <div class="preview-container">
    <div class="cards-row">
      <div class="preview-aria preview-aria1">
        <div class="card-title">Help</div>
      </div>

      <div class="preview-aria preview-aria2">
        <div class="card-title">Busy</div>
      </div>

      <div class="preview-aria preview-aria3">
        <div class="card-title">Working</div>
      </div>
    </div>

    <div class="preview-aria text-aria">
      <h3>Text Cursor Preview</h3>

      <p>Text Area. Move mouse on the text to see the effect.</p>
      <span>Text Area. Move mouse on the text to see the effect.</span>
      <p>Text Area. Move mouse on the text to see the effect.</p>
      <span>Text Area. Move mouse on the text to see the effect.</span>

      <textarea rows="4" type="text" :placeholder="textAriaTips" />
    </div>
  </div>

  <tip>
    预览 ani 文件来源于B站UP Moos柚眠：
    【【初音未来】鼠标指针，来喽！-哔哩哔哩】
    https://www.bilibili.com/video/BV1bG4y1x7YY/
  </tip>
</template>

<script setup>
import { setANICursor, setANICursorWithGroupElement } from "ani-cursor.js";

const controller = setANICursor(
  "html",
  "/ani-cursor-preview/ani/Main.ani",
  "auto",
  32,
  32
);

console.log(controller);

controller.ready.then(() => {
  console.log("Main cursor ready");
});

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
`;
</script>

<style lang="scss">
body {
  margin: 0;
  background: linear-gradient(180deg, #f8fafc 0%, #eef2f7 50%, #e7edf5 100%);
}

#app {
  width: 1400px;
  margin: 0 auto;
  padding: 40px 0 80px;

  font-family: Inter, "Segoe UI", Helvetica, Arial, sans-serif;

  color: #2c3e50;
}

.hero {
  text-align: center;
  margin-bottom: 60px;
}

.hero h1 {
  margin: 0;
  font-size: 4rem;
  font-weight: 800;
  letter-spacing: -2px;

  background: linear-gradient(135deg, #2563eb, #7c3aed);

  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.hero-desc {
  margin-top: 18px;
  font-size: 1.2rem;
  color: #64748b;
}

.version-tip {
  margin-top: 12px;
  color: #94a3b8;
  font-size: 14px;
}

.preview-container {
  display: flex;
  flex-direction: column;
  gap: 30px;
}

.cards-row {
  display: flex;
  gap: 30px;
  width: 100%;
}

.preview-aria {
  background: rgba(255, 255, 255, 0.8);

  backdrop-filter: blur(16px);

  border: 1px solid rgba(255, 255, 255, 0.5);

  border-radius: 24px;

  box-shadow: 0 10px 30px rgba(15, 23, 42, 0.08), 0 1px 3px rgba(15, 23, 42, 0.05);

  transition: transform 0.25s ease, box-shadow 0.25s ease;
}

.preview-aria:hover {
  transform: translateY(-4px);

  box-shadow: 0 20px 50px rgba(15, 23, 42, 0.12), 0 4px 10px rgba(15, 23, 42, 0.08);
}

.preview-aria1,
.preview-aria2,
.preview-aria3 {
  flex: 1;
  height: 180px;

  display: flex;
  justify-content: center;
  align-items: center;
}

.preview-aria1 {
  background: linear-gradient(
    135deg,
    rgba(59, 130, 246, 0.12),
    rgba(255, 255, 255, 0.8)
  );
}

.preview-aria2 {
  background: linear-gradient(
    135deg,
    rgba(245, 158, 11, 0.12),
    rgba(255, 255, 255, 0.8)
  );
}

.preview-aria3 {
  background: linear-gradient(
    135deg,
    rgba(34, 197, 94, 0.12),
    rgba(255, 255, 255, 0.8)
  );
}

.card-title {
  font-size: 2rem;
  font-weight: 700;
}

.text-aria {
  padding: 40px;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.text-aria h3 {
  margin-top: 0;
  margin-bottom: 20px;
  font-size: 1.8rem;
  width: 60%;
}

.text-aria p,
.text-aria span {
  display: block;
  margin: 8px 0;
  color: #475569;
  width: 60%;
}

.text-aria textarea {
  width: 900px;
  height: 220px;

  margin-top: 25px;
  padding: 18px;

  border-radius: 16px;
  border: 1px solid #dbe3ef;

  background: #fafcff;

  font-family: Consolas, Monaco, monospace;

  font-size: 14px;
  line-height: 1.6;

  resize: vertical;

  transition: all 0.2s ease;
}

.text-aria textarea:focus {
  outline: none;

  border-color: #3b82f6;

  box-shadow: 0 0 0 4px rgba(59, 130, 246, 0.15);
}

tip {
  display: block;

  margin-top: 40px;

  padding: 24px;

  border-radius: 20px;

  background: rgba(255, 255, 255, 0.75);

  border: 1px solid rgba(255, 255, 255, 0.5);

  box-shadow: 0 10px 30px rgba(15, 23, 42, 0.08);

  text-align: center;

  line-height: 1.8;

  color: #64748b;
}
</style>
```
