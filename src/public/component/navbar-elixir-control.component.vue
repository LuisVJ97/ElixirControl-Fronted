<script>
import LanguageSwitcher from "./language-switcher.component.vue";

export default {
  name: "navbar-elixir-control",

  components: {LanguageSwitcher},

  title: 'Elixir Control',

  data() {
    return {
      drawer: true,
      items: [
        { label: 'title-Home',        to: "/productor/home",                icon: 'pi pi-home' },
        { label: 'title-Inventory',   to: "/productor/inventory",           icon: 'pi pi-receipt' },
        { label: 'title-Winemaking',  to: '/productor/winemaking-process',  icon: 'pi pi-spinner-dotted' },
        { label: 'title-My Clients',  to: '/productor/clients',             icon: 'pi pi-user' },
        { label: 'title-My Orders',   to: '/productor/orders/history',      icon: 'pi pi-list-check' },
        { label: 'title-My Products', to: '/productor/products',            icon: 'pi pi-tags' },
        { label: 'title-Support',     to: '/productor/Support',             icon: 'pi pi-wrench' },
      ]
    }
  },


  created() {
    console.log('Navbar created');
  }

}
</script>

<template>


  <pv-toast/>

  <section>
    <pv-toolbar class="w-full fixed top-0 left-0 pr-8 pl-8 pb-2.8 z-1" style="background-color:#8B0000; margin-top: 0;">
      <template #start>
        <img src="../../assets/img/logo-elixir-control.png" height="50px" alt="Logo Elixir Control"/>
      </template>

      <template #center>
      </template>

      <template #end>
        <div>
          <language-switcher/>
        </div>
      </template>
    </pv-toolbar>
  </section>



  <section>
    <pv-card class="h-screen fixed top-0 left-0 pr-8 pl-8 z-1" style="margin-top:80px;
    background-color:#8B0000; height:40px; color:white">

      <template #title>
        <p class="pt-1"></p>
      </template>

      <template #subtitle>
        <div class="flex flex-column">
          <router-link v-for="item in items" :key="item.label" v-slot="{navigate, href}" :to="item.to" custom>
            <pv-button class="md:hover:text-color-secondary p-button-text text-white m-2 justify-content-start "
                       :href="href"
                       @click="navigate" >
              <i :class="item.icon" style="font-size: 1.3rem;" />
              {{ $t(item.label) }}
            </pv-button>
          </router-link>
        </div>
      </template>

      <template #footer>
        <span class="w-full text-center"> © 2024 Elixir Control</span>
      </template>
    </pv-card>
  </section>

  <section class="z-0" style="margin-top: 8%; margin-left:320px">
    <router-view/>
  </section>


</template>

<style scoped>

</style>