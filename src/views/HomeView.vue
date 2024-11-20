<template>
  <div class="home">
    <HeaderCompo class="header"></HeaderCompo>
    <div class="main-content">
      <SidebarCompo class="left-sidebar"></SidebarCompo>
      <ContentCompo class="content"></ContentCompo>
      <SidebarCompo class="right-sidebar"></SidebarCompo>
    </div>
    <FooterCompo class="footer"></FooterCompo> 
  </div> 
</template>

<script>
// @ is an alias to /src
import ContentCompo from '@/components/ContentCompo.vue';
import FooterCompo from '@/components/FooterCompo.vue';
import HeaderCompo from '@/components/HeaderCompo.vue';
import SidebarCompo from '@/components/SidebarCompo.vue';

export default {
  name: 'HomeView',
  components: {
    HeaderCompo,
    SidebarCompo,
    ContentCompo,
    SidebarCompo,
    FooterCompo
  }
}
</script>

<style scoped>
  .main-content {
      flex:1;
      display: flex;
      justify-content: center;
      align-items: center;
    }

  .header, .footer, .left-sidebar, .right-sidebar {
    background: gray;
    margin: 5px;
    border-radius: 10px;
  }

  @media all and (min-width: 600px) {
    .left-sidebar, .right-sidebar { flex: 1 0 0; }
  }
    
  @media all and (min-width: 800px) {
      .main-content    { flex: 3 0px; }
      .left-sidebar { order: 0; } 
      .main-content    { order: 2; }
      .right-sidebar { order: 3; }
      .footer  { order: 4; }
  }
</style>
