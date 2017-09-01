<template>
  <div class="hello">
    <div class="content-wrapper">
    <h1>Welcome to the IXD-lab "Resource Base" Server</h1>
    <h2>This server is build for speeding up web resource loading from other servers</h2>
    <a @click.prevent="$router.push({ name: 'Content' })">see the resource list</a>
    <a @click.prevent="$router.push({ name: 'Upload' })" disable>upload resources</a>
    <a class="iconfont icon-github" href="https://github.com/pierrejacques/IXD-lab-resource-base" target="_blank"></a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'hello',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
  .hello {
    height: 80vh;
    display: flex;
  }
  .content-wrapper {
    margin: auto;
  }
h1, h2 {
  font-weight: normal;
}

a {
  margin: 30px;
  color: #42b983;
  cursor: pointer;
}
  a:hover {
    text-decoration: underline;
  }
  a[disable] {
    pointer-events: none;
    filter: grayscale();
    cursor: none;
  }
  .icon-github {
    position: absolute;
    top: 0;
    right: 0;
    font-size: 2em;
    color: #2c3e50;
  }
</style>
