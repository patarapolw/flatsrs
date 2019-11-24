```html
<style>
.speak {
  color: blue;
  cursor: pointer;
  text-decoration: underline;
}
</style>
<script>
window.speak = function(s, lang) {
  const u = new SpeechSynthesisUtterance(s);
  u.lang = lang;
  speechSynthesis.speak(u);
};

window.revealMdPlugins = window.revealMdPlugins || {};
window.revealMdPlugins.markdown = window.revealMdPlugins.markdown || {};
window.revealMdPlugins.markdown.speakOnly = {
  type: "lang",
  regex: /\^\^speak-only (.+)\n/g,
  replace: (p0, p1) => {
    return `<span class="speak" onclick="speak('${p1}', 'zh-CN')">Click to speak</span>`
  }
};
</script>
```