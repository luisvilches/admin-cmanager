<template>
  <div class="app">
    <AppHeader fixed>
      <SidebarToggler class="d-lg-none" display="md" mobile />
      <b-link class="navbar-brand" to="#">
        <h2>Cardumen</h2>
      </b-link>
      <SidebarToggler class="d-md-down-none" display="lg" />
      <b-navbar-nav class="ml-auto">
        <b-nav-item class="d-md-down-none">
          <i class="icon-bell"></i>
          <b-badge pill variant="danger">5</b-badge>
        </b-nav-item>
        <b-nav-item class="d-md-down-none">
          <i class="icon-list"></i>
        </b-nav-item>
        <b-nav-item class="d-md-down-none">
          <i class="icon-location-pin"></i>
        </b-nav-item>
        <AppHeaderDropdown right no-caret>
          <div>
          <template slot="button-content">
            <img src="static/img/avatars/6.jpg" class="img-avatar" alt="admin@bootstrapmaster.com" />
          </template>
          <b-dropdown-item><i class="fa fa-user" /> Perfil</b-dropdown-item>
          <b-dropdown-item><i class="fa fa-lock" /> Cerrar Sesion</b-dropdown-item>
          </div>
        </AppHeaderDropdown>
      </b-navbar-nav>
      <!--AsideToggler class="d-none d-lg-block" /-->
      <!--<AsideToggler class="d-lg-none" mobile />-->
    </AppHeader>
    <div class="app-body">
      <AppSidebar fixed>
        <SidebarHeader/>
        <SidebarForm/>
        <SidebarNav :navItems="nav"></SidebarNav>
        <SidebarFooter/>
        <SidebarMinimizer/>
      </AppSidebar>
      <main class="main">
        <breadcrumb :list="list"/>
        <div class="container-fluid">
          <router-view></router-view>
        </div>
      </main>
      <!--AppAside fixed>
        
        <DafaultAside/>
      </AppAside-->
    </div>
    <TheFooter>
      <!--footer-->
    </TheFooter>
  </div>
</template>

<script>
import nav from '../_nav'
import { Header as AppHeader, HeaderDropdown as AppHeaderDropdown, SidebarToggler, Sidebar as AppSidebar, SidebarFooter, SidebarForm, SidebarHeader, SidebarMinimizer, SidebarNav, Aside as AppAside, AsideToggler, Footer as TheFooter, Breadcrumb } from '@coreui/vue'
// import { Header as AppHeader, HeaderDropdown as AppHeaderDropdown, SidebarToggler, Sidebar as AppSidebar, SidebarFooter, SidebarForm, SidebarHeader, SidebarMinimizer, SidebarNav, Aside as AppAside, AsideToggler, Breadcrumb } from '../components/'
// import { Footer as TheFooter } from '@coreui/vue'
import DafaultAside from './DafaultAside'

export default {
  name: 'full',
  components: {
    AsideToggler,
    AppHeader,
    AppHeaderDropdown,
    AppSidebar,
    AppAside,
    TheFooter,
    Breadcrumb,
    DafaultAside,
    SidebarForm,
    SidebarFooter,
    SidebarToggler,
    SidebarHeader,
    SidebarNav,
    SidebarMinimizer
  },
  data () {
    return {
      nav: nav.items,
      itemsCount: 42
    }
  },
  computed: {
    name () {
      return this.$route.name
    },
    list () {
      return this.$route.matched
    }
  }
}
</script>

<style >
  .img-avatar{
    margin-right: 40px!important;
  }
</style>
