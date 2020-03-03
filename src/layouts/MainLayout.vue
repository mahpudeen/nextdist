<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated class="back-head">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />
        

        <q-toolbar-title>
          602 OPERASI CANVAS
        </q-toolbar-title>
          <q-separator vertical inset color="white"/>
        <div class="fs-10 mar-head-sep">
          PT. SURYA PANGAN SEJAHTERA, BEKASI
        </div>
          <q-separator vertical inset color="white"/>
        <div class="fs-10 mar-head-sep">
          Week 7 2020-02-14
        </div>
          <q-separator vertical inset color="white"/>
        <div class="fs-10 mar-head-sep">
          BM 0-0
        </div>
          <q-separator vertical inset color="white"/>
        <div>
          <q-btn
            flat
            dense
            icon="email"
            @click="leftDrawerOpen = !leftDrawerOpen"
          />
          <q-btn
            flat
            dense
            icon="people"
            @click="leftDrawerOpen = !leftDrawerOpen"
          />
          <q-btn
            flat
            dense
            icon="person"
            @click="leftDrawerOpen = !leftDrawerOpen"
          />
          <q-btn
            flat
            dense
            icon="home"
            @click="leftDrawerOpen = !leftDrawerOpen"
          />
          <q-btn
            flat
            dense
            icon="view_module"
            @click="leftDrawerOpen = !leftDrawerOpen"
          />
          <q-btn
            flat
            dense
            icon="alarm"
            @click="leftDrawerOpen = !leftDrawerOpen"
          />
          <q-btn
            flat
            dense
            icon="star"
            @click="leftDrawerOpen = !leftDrawerOpen"
            style="color:gold"
          />
          <q-btn
            flat
            dense
            icon="power_settings_new"
            @click="logout()"
          />
        </div>
      </q-toolbar>
    </q-header>
    <q-header elevated class="back-head2 back-head">
      <q-toolbar>
        
        <q-btn-dropdown style="color:black" flat no-caps v-for="(menuItem, index) in menuList[menuIndex].children" :key="index">
          <template v-slot:label>{{menuItem.label}}</template>
          <q-list v-for="(menuItemChild, index) in menuItem.children" :key="index" class="bg-primary black">
            <q-item clickable v-close-popup @click="onItemClick" >
              <q-item-section>
                <q-item-label>{{menuItemChild.label}}</q-item-label>
              </q-item-section>
            </q-item>
          </q-list>
        </q-btn-dropdown>
        

        <q-toolbar-title>
        </q-toolbar-title>
        

        <div>
        </div>
      </q-toolbar>
    </q-header>
    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-blue-grey-10"
    >
      <q-list>
        <q-item-label
          header
          style="font-size:18px; color:#948654; margin-bottom:-8px"
        >
          MAIN MENU
        </q-item-label>
        <!-- <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        /> -->
      </q-list>
      <q-list v-for="(menuItem, index) in menuList" :key="index">

            <q-item clickable v-ripple style="background-color:#948654;margin:5px;font-size:10px" @click="changeMenu(index)">
              <!-- <q-item-section avatar>
                <q-icon :name="menuItem.icon" />
              </q-item-section> -->
              <q-item-section>
                {{ menuItem.label }}
              </q-item-section>
            </q-item>


          </q-list>
    </q-drawer>

    <q-page-container class="back-head2">
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import EssentialLink from 'components/EssentialLink'
const menuList = [
{ 
  label : "PERSEDIAAN [STOCK MONITORING]",
  children : [
    {
      label : "Kontrol Stock",
      children : [
        {
          label : "Draft"
        },
        {
          label : "Mutasi"
        },
        {
          label : "Opname"
        },
        {
          label : "Laporan"
        },
      ]
    },
    {
      label : "Operasi Canvas",
      children : [
        {
          label : "Stock"
        }
      ]
    }
  ]
},
{
  label : "PEMBELIAN [PURCHASES]",
  children : [
    {
      label : "Pembelian",
      children : [
        {
          label : "Order"
        },
        {
          label : "Terima"
        },
        {
          label : "Laporan"
        },
      ]
    }
  ]
},
{label : "HUTANG [PAYABLES]"},
{label : "PENJUALAN [SALES]"},
{label : "PIUTANG [RECEIVABLES]"},
{label : "DISTRIBUTION [SALES ANALYSIS & REPORT]"},
{label : "PROMOSI [PROMOTION SETUP]"},
{label : "PAJAK [TAX]"},
{label : "PEMBUKUAN [ACCOUNT FEE]"},
{label : "KEUANGAN [FINANCIAL & LEDGER]"},
{label : "INTERFACE [INTERFACE]"},
{label : "MOBILITY [SALES FORCE AUTOMATION]"},


]


export default {
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  data () {
    return {
      menuIndex : 0,
      menuList,
      leftDrawerOpen: false,
      essentialLinks: [
        {
          title: 'Docs',
          caption: 'quasar.dev',
          icon: 'school',
          link: 'https://quasar.dev'
        },
      ]
    }
  },
  methods : {
    changeMenu(index) {
      this.menuIndex = index;
    },
    onItemClick() {

    },
    logout() {
        this.$router.push('/login')
    }
  }
}
</script>
