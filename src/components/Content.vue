<template>
  <div class="content">
    <ul class="column" v-for="(col, layer) in content">
      <div v-for="(item, idx) in col">
        <file v-if="typeof item === 'string'" :str="item"></file>
        <li v-else class="folder" :class="{selected:selected[layer] === idx}" @click="unfold(layer, idx)"> + {{item.folder}}</li>
      </div>
    </ul>
    <div class="banner">
      <h1>IXD lab Resource Base</h1>
      <a @click.prevent="$router.push({ name: 'Hello' })">back to Home</a>
    </div>
  </div>
</template>

<script>
import file from './file'
export default {
  name: 'Content',
  components: {
    file,
  },
  data() {
    return {
      content: [],
      selected: [],
    }
  },
  created() {
    // xhr拿数据
    const xhr = new XMLHttpRequest()
    const stateChange = () => {
      if (xhr.readyState === 4) {
        if (xhr.status === 200) {
          this.content.push(JSON.parse(xhr.response))
        } else {
          console.error('fail to load content')
        }
      }
    }
    xhr.onreadystatechange = stateChange
    xhr.open('GET', '/static/content.json', true)
    xhr.send(null)
  },
  methods: {
    unfold(layer, idx) {
      this.content = this.content.slice(0, layer + 1)
      this.selected = this.selected.slice(0, layer + 1)
      this.content.push(this.content[layer][idx].content)
      this.selected[layer] = idx
    }
  }
}

</script>

<style lang="css" scoped>
  .content {
    display: flex;
    height: 100vh;
  }
  .column {
    width: 200px;
    text-align: left;
    height: 100%;
    overflow: auto;
    border-right: 1px solid silver;
    background: linear-gradient(white 30%, transparent),
              radial-gradient(at 50% 0, rgba(0, 0, 0, .3),
                 transparent 70%),
              linear-gradient(to top, white 30%, transparent) bottom,
              radial-gradient(at bottom, rgba(0, 0, 0, .3),
                 transparent 70%) bottom;
    background-repeat: no-repeat;
    background-size: 100% 50px, 100% 15px, 100% 50px, 100% 15px;
    background-attachment: local, scroll, local, scroll;
  }
  .column::-webkit-scrollbar {
    width: 0;
  }
  ul {
    padding: 0;
    margin: 0;
  }
  .folder.selected {
    color: white;
    background: #677781;
  }
  .folder {
    cursor: pointer;
    color: black;
  }
  .banner {
    margin: auto;
    flex-grow: 1;
  }
</style>