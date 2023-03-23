<template>
  <div id="app">
    <terminal :ref="name" :name="name" :title="title" :context="context" :commandStore="cmdStore"  @execCmd="onExecCmd" :init-log="initLog"></terminal>
  </div>
</template>

<script>
import Terminal from "vue-web-terminal"

export default {
  name: 'App',
  components: {
    Terminal
  },
  data() {
    return {
      name:'my-coder-life',
      context: '/my-info',
      title: '孤独的键',
      initLog: [
        {
          content: '正在启动，初始化中...',
          type: 'normal',
        },
        {
          content: 'cd 孤独的键',
          type: 'normal',
          class:'info',
          tag: 'System'
        },
        {
          content: '准备载入 孤独的键 ...',
          type: 'normal',
          class:'info',
          tag: 'System'
        },
        {
          content: 'Loading succeeded，let me introduce myself.',
          type: 'normal',
          class:'success',
          tag: 'System'
        },
        {
          "type": "table",
          "content": {
            "head": [
              "姓名",
              "性别",
              "年龄",
              "邮箱",
            ],
            "rows": [
              [
                "雾山",
                "男",
                "29",
                "mistyhills53@gmail.com",
              ],
            ]
          }
        }
      ],
      cmdStore:[
        {
          key: "fullscreen",
          group: "diy",
          usage: "fullscreen",
          description: "切换全屏模式"
        },
        {
          key: "img",
          group: "diy",
          usage: "img",
          description: "需要用图床？"
        },
        {
          key: "music",
          group: "diy",
          usage: "music",
          description: "需要听音乐？"
        },
        {
          key: "talk",
          group: "diy",
          usage: "talk",
          description: "需要跟我交流？"
        },
        {
          key: "blog",
          group: "diy",
          usage: "blog",
          description: "需要刷博客？"
        },
        {
          key: "nav",
          group: "diy",
          usage: "nav",
          description: "需要访问我所有网站？"
        }
      ]
    }
  },
  methods: {
    onExecCmd(key, command, success, failed) {
      const terminal = this.$refs[this.name]
      if (key === 'fail') {
        failed('未知指令!!!')
      }
      else if(key === 'fullscreen') {
        terminal.fullscreen();
        success({
          type: "normal",
          class: "success",
          content: "ok"
        });
      }
      else if(key === 'music') {
        window.open('https://music.mistyhill.ml');
        success({
          type: "normal",
          class: "success",
          content: "ok"
        });
      }
      else if(key === 'talk') {
        window.open('https://tg.mistyhill.ml/#856146798');
        success({
          type: "normal",
          class: "success",
          content: "ok"
        });
      }
      else if(key === 'img') {
        window.open('https://imgs.mistyhill.ml');
        success({
          type: "normal",
          class: "success",
          content: "ok"
        });
      }
      else if(key === 'blog') {
        window.open('https://blog.mistyhill.ml');
        success({
          type: "normal",
          class: "success",
          content: "ok"
        });
      }
      else if(key === 'nav') {
        window.open('https://nav.mistyhill.ml');
        success({
          type: "normal",
          class: "success",
          content: "ok"
        });
      }
      else {
        let allClass = ['success', 'error', 'system', 'info', 'warning'];

        let clazz = allClass[Math.floor(Math.random() * allClass.length)];
        success({
          type: 'normal',
          class: clazz,
          tag: "随机标签：" + clazz,
          content: command
        })
      }
    }
  }
}
</script>

<style>
body, html, #app {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
}
</style>
