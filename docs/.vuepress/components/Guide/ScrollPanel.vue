<template>
  <div class="wrapper">
    <div class="title"> {{config.title}}</div>
    <div class="demo-area">
      <div class="parent">
        <vue-scroll :ops="ops" ref="vs">
          <div class="child"></div>
        </vue-scroll>
      </div>
      <div class="operation">
        <vue-scroll>
          <table class=" ">
            <tr>
              <td>Animation</td>
              <td>
                <select v-model="ops.scrollPanel.easing">
                  <option v-for="easing in easings" :value="easing">
                    {{easing}}
                  </option>
                </select>
              </td>
            </tr>
            <tr>
              <td>Speed</td>
              <td>

                <input type="range" :min="300" :max="2000" :step="50" v-model="ops.scrollPanel.speed">{{ops.scrollPanel.speed}}

              </td>
            </tr>
            <tr>
              <td colspan="2">
                <button @click="randomScroll">Scroll to a random position</button>
              </td>
            </tr>
          </table>
        </vue-scroll>
      </div>
    </div>

  </div>
</template>

<script>
const easings = [
  'easeInQuad',
  'easeOutQuad',
  'easeInOutQuad',
  'easeInCubic',
  'easeOutCubic',
  'easeInOutCubic',
  'easeInQuart',
  'easeOutQuart',
  'easeInOutQuart',
  'easeInQuint',
  'easeOutQuint',
  'easeInOutQuint'
];

export default {
  props: {
    lang: {
      tyoe: String,
      default: 'en'
    }
  },
  computed: {
    config() {
      return this.i18n[this.lang];
    }
  },
  data() {
    return {
      easings,
      ops: {
        scrollPanel: {
          easing: 'easeInQuad',
          speed: 800
        }
      },
      i18n: {
        zh: {
          title: '调整速度和动画查看效果。'
        },
        en: {
          title: 'Adjust speed and animation viewing effect.'
        }
      }
    };
  },
  methods: {
    randomScroll() {
      const x = Math.random() * 800;
      const y = Math.random() * 800;
      this.$refs['vs'].scrollTo({
        x,
        y
      });
    }
  }
};
</script>

<style lang="stylus" scoped>
.wrapper {
  margin-top: 20px;
  width: 100%;
  background-color: #e2e1dd;
  padding: 10px;
  color: #007b9c;

  .title {
    height: 4rem;
    line-height: 4rem;
    text-align: center;
    font-size: 1rem;
    background-color: #fbabbd;
  }

  .demo-area {
    width: 100%;
    margin: auto;
    margin-top: 1rem;
    display: flex;
    background-color: #90d6f1;

    .parent {
      width: 60%;
      height: 12rem;

      /deep/ .child {
        width: 1000px;
        height: 1000px;
        background: linear-gradient(45deg, rgb(0, 159, 255), rgb(236, 47, 75));
      }
    }

    .operation {
      height: 12rem;
      width: 40%;
      background-color: #d5d5d7;

      table {
        display: table;
        width: 100%;

        td {
          text-align: center;

          button {
            white-space: nowrap;
          }
        }
      }
    }
  }
}
</style>
