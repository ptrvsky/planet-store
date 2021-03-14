<template>
  <div class="header">
    <div class="header-content">
      <div class="side left">
        <span class="material-icons planet">public</span>
        <span class="name">PLANET SHOP</span>
      </div>
      <div class="side right">
        <a href="/" class="link">About us</a>
        <a href="/" class="link">Products</a>
        <a href="/" class="link">Sign up</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Header'
}
</script>

<style scoped lang="scss">

.header {
  position: fixed;
  min-width: 100%;
  height: 80px;
  max-height: 80px;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 2;

  .header-content {
    max-width: 1280px;
    width: 1280px;
    display: flex;
    justify-content: space-between;

    .side {
      display: flex;
      align-items: center;

      .planet {
        color: #ff00a1;
        font-size: 3em;
      }

      .name {
        color: #f5f5f5;
        font-size: 2em;
        font-weight: 600;
        margin-left: 10px;
      }

      .link {
        font-size: 1.1em;
        margin-left: 40px;
        text-decoration: none;
        color: whitesmoke;
      }
    }
  }
}
</style>