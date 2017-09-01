<template>
  <div class="hello">
    <div class="content-wrapper">
    <h1>Welcome to the IXD-lab "Resource Base" Server</h1>
    <h2>This server is build for speeding up web resource loading from other servers</h2>
    <a @click.prevent="$router.push({ name: 'Content' })">see the resource list</a>
    <a @click.prevent="$router.push({ name: 'Upload' })">upload resources</a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'hello',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .hello {
    height: 70vh;
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
</style>
