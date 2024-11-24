<template>
  <div class="home">
    <HeaderCompo class="header"></HeaderCompo>
    <div class="main-content">
      <!-- Left Sidebar -->
      <SidebarCompo class="left-sidebar"></SidebarCompo>

      <!-- Content Area -->
      <ContentCompo class="content"></ContentCompo>

      <!-- Right Sidebar -->
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
    FooterCompo
  }
}
</script>

<style scoped>
/* Make the home container take the full height of the viewport */
.home {
  display: flex;
  flex-direction: column;
  height: 100vh; /* Full height of the viewport */
}

/* Ensure the main content area takes up available space */
.main-content {
  display: flex;
  flex: 1; /* This makes the main content area grow and fill available space */
  justify-content: center;
  align-items: flex-start;
  gap: 10px;
  margin-bottom: 20px; /* Add space for the footer */
}

/* The header and footer are already set up */
.header, .footer, .left-sidebar, .right-sidebar {
  background: gray;
  margin: 10px;
  border-radius: 10px;
  padding: 20px;
}


/* Adjust the layout for small screens */
@media all and (min-width: 600px) {
  .left-sidebar, .right-sidebar {
    flex: 1 0 0; /* These will take up equal width on larger screens */
  }
}

/* Adjust layout for medium screens and up */
@media all and (min-width: 800px) {
  .main-content {
    flex: 3 0px; /* The content area will take up more space */
  }

  .left-sidebar {
    order: 0;
  }

  .main-content {
    order: 2;
  }

  .right-sidebar {
    order: 3;
  }

  .footer {
    order: 4;
  }
}
/* Ensure the sidebars are placed at the bottom */
.left-sidebar, .right-sidebar {
  display: flex;
  flex-direction: column;
  justify-content: flex-end; /* Align children to the bottom of the sidebar */
  height: 99%; /* Make sure sidebars stretch to fill the available height */
}

</style>
