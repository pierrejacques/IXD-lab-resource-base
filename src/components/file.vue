<template>
  <span>
    <li v-for="item in list">{{item}}</li>
  </span>
</template>

<script>
const isFolded = str => /\[*\]/.test(str)
export default {
  name: 'file',
  props: [
    'str',
  ],
  computed: {
    list() {
      const list = []
      if (isFolded(this.str)) {
        const startIdx = /\[/.exec(this.str).index
        const midIdx = /\:/.exec(this.str).index
        const endIdx = /\]/.exec(this.str).index
        const start = parseInt(this.str.slice(startIdx + 1, midIdx), 10)
        const end = parseInt(this.str.slice(midIdx + 1, endIdx), 10)
        const pre = this.str.slice(0, startIdx)
        const post = this.str.slice(endIdx + 1)
        for (let i = start; i <= end; i++) {
          list.push(`${pre}${i}${post}`)
        }
      } else {
        list.push(this.str)
      }
      return list
    }
  }
}

</script>

<style lang="css" scoped>
  li {
    color: #63848e;
  }
</style>