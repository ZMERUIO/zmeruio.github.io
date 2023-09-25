<template>
  <LuckyWheel
      ref="myLucky"
      width="300px"
      height="300px"
      :prizes="prizes"
      :blocks="blocks"
      :buttons="buttons"
      @start="startCallback"
      @end="endCallback"
  />
</template>

<script>
export default {
  data() {
    return {
      blocks: [{padding: '13px', background: '#617df2'}],
      prizes: [
        {fonts: [{text: '0', top: '10%'}], background: '#e9e8fe'},
        {fonts: [{text: '1', top: '10%'}], background: '#b8c5f2'},
        {fonts: [{text: '2', top: '10%'}], background: '#e9e8fe'},
        {fonts: [{text: '3', top: '10%'}], background: '#b8c5f2'},
        {fonts: [{text: '4', top: '10%'}], background: '#e9e8fe'},
        {fonts: [{text: '5', top: '10%'}], background: '#b8c5f2'},
      ],
      buttons: [{
        radius: '25%',
        background: '#8a9bf3',
        pointer: true,
        fonts: [{text: '开始', top: '-10px'}]
      }],
      takeout: [
        "炸鸡",
        "披萨",
        "意大利面",
        "烤肉",
        "麻辣烫",
        "汉堡",
        "烤玉米",
        "炒饭",
        "饺子",
        "烤鱼",
        "牛排",
        "炒面",
        "煲仔饭",
        "盖浇饭",
        "芝士焗饭",
        "麻辣香锅",
        "煎饼果子",
        "豆腐脑",
        "烤串",
        "肉夹馍",
        "黄焖鸡米饭",
        "牛肉面",
        "煲汤",
        "猪脚饭",
        "叉烧饭",
        "红烧肉",
        "卤肉饭",
        "鸡肉卷",
        "墨西哥卷饼",
        "糖醋排骨",
        "酸菜鱼",
        "麻辣小龙虾",
        "石锅拌饭",
        "烤冷面",
        "手抓饼",
        "炒河粉",
        "煲汤",
        "红烧鱼",
        "糖醋里脊",
        "红烧茄子煲",
        "海底捞火锅",
        "水煮鱼",
        "红烧排骨",
        "清蒸鲈鱼",
        "麻辣火锅",
        "日式寿司",
        "烤鸭",
        "烧烤",
        "涮串",
        "新疆菜"
      ]
    }
  },
  created() {
    this.initPrizes()
  },
  methods: {
    // 点击抽奖按钮会触发star回调
    startCallback() {
      // 调用抽奖组件的play方法开始游戏
      this.$refs.myLucky.play()
      // 模拟调用接口异步抽奖
      setTimeout(() => {
        // 假设后端返回的中奖索引是0
        const index = Math.floor(Math.random() * 50)
        // 调用stop停止旋转并传递中奖索引
        this.$refs.myLucky.stop(index)
      }, 2000)
    },
    // 抽奖结束会触发end回调
    endCallback(prize) {
      console.log(prize)
    },
    initPrizes() {
      this.prizes = []
      let colors = this.generateRandomGradientColors(50)
      for (let i = 0; i < 50; i++) {
        let item = {
          fonts: [{text: this.takeout[i], top: '10%', fontSize: '10px'}],
          background: i % 2 === 0 ? '#e9e8fe' : '#b8c5f2'
        }
        this.prizes.push(item)
      }
    },
    generateRandomGradientColors(count) {
      const letters = '0123456789ABCDEF';
      const colors = [];
      for (let i = 0; i < count; i++) {
        let color = '#';
        for (let j = 0; j < 6; j++) {
          color += letters[Math.floor(Math.random() * 16)];
        }
        colors.push(color);
      }
      return colors;
    }
  }
}
</script>