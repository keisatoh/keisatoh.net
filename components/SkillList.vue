<template>
  <div class="skillList">
    <div class="proficiency">
      <p
        class="proficiency__message"
        :class="hoverFlag ? 'messageOn' : 'messageOff'"
      >
        {{ message }}
      </p>
      <div class="proficiency__label">
        <label
          @mouseover="mouseOverAction('すべて表示します')"
          @mouseleave="mouseLeaveAction"
        >
          <input v-model="proficiency" type="radio" value="" />👉
        </label>
        <label
          @mouseover="mouseOverAction('たのしくかけます')"
          @mouseleave="mouseLeaveAction"
        >
          <input v-model="proficiency" type="radio" value="3" />🙂
        </label>
        <label
          @mouseover="mouseOverAction('がんばってかきます')"
          @mouseleave="mouseLeaveAction"
        >
          <input v-model="proficiency" type="radio" value="2" />😕
        </label>
        <label
          @mouseover="mouseOverAction('べんきょうしてます')"
          @mouseleave="mouseLeaveAction"
        >
          <input v-model="proficiency" type="radio" value="1" />😖
        </label>
      </div>
    </div>
    <div class="flex-container">
      <div
        v-for="image in filterByProficiency"
        :key="image.index"
        class="flex-item"
      >
        <img :src="image.src" alt="" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: '表示を切り替えられます',
      hoverFlag: true,
      proficiency: '',
      images: [
        {
          index: 1,
          src: require('@/assets/images/html-5.svg'),
          proficiency: '3',
        },
        {
          index: 2,
          src: require('@/assets/images/css-3.svg'),
          proficiency: '3',
        },
        {
          index: 3,
          src: require('@/assets/images/javascript.svg'),
          proficiency: '3',
        },
        {
          index: 4,
          src: require('@/assets/images/typescript-icon.svg'),
          proficiency: '1',
        },
        {
          index: 5,
          src: require('@/assets/images/vue.svg'),
          proficiency: '2',
        },
        {
          index: 6,
          src: require('@/assets/images/nuxt.svg'),
          proficiency: '2',
        },
        {
          index: 7,
          src: require('@/assets/images/tailwindcss-icon.svg'),
          proficiency: '3',
        },
        {
          index: 8,
          src: require('@/assets/images/figma.svg'),
          proficiency: '3',
        },
      ],
    }
  },
  computed: {
    filterByProficiency() {
      return this.images.filter(
        (logo) => !logo.proficiency.indexOf(this.proficiency)
      )
    },
  },
  methods: {
    mouseOverAction(note) {
      this.hoverFlag = true
      this.message = note
      // filterByProficiency()
    },
    mouseLeaveAction() {
      this.hoverFlag = false
    },
  },
}
</script>


<style lang="scss" scoped>
.messageOn {
  visibility: visible;
}
.messageOff {
  visibility: hidden;
}

h2 {
  font-family: $font-base;
  font-size: rem(25);
  margin-bottom: 0.25em;
}

.flex-container {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 5px;
  margin-top: 2em;
}

.flex-item {
  margin: 0 32px 0 0;
  // height: 50px;
}

.proficiency {
  text-align: left;
  width: max-content;
}
.proficiency__message {
  color: black;
  width: max-content;
  border-radius: .5em;
  padding: 0 1em 0 1em;
  border: 1px solid #2A293D;
  box-shadow: 0 1px 1px 0 rgba(0, 0, 0, .5);
  margin-top: 1em;
}
.proficiency__label {
  margin-top: 1em;
}
.proficiency label {
  cursor: pointer;
  font-size: rem(28);
  margin: 0 0 0 1rem;
}
.proficiency input[type='radio'] {
  opacity: 0;
  -webkit-appearance: none;
  appearance: none;
  position: absolute;
}

.proficiency__label label:first-child {
  padding-left: 0;
  margin: 0;
}
</style>