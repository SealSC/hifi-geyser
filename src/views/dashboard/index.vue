<template>
  <div class="dashboard-container">
    <div class="row">
      <div class="col text-center">
        <img class="home-logo" :src="'/static/logo/logo-long.png'" alt=""/>
      </div>
    </div>
    <div class="row">
      <div class="col text-center welcome-tit">{{ $t("common.welcome") }}</div>
    </div>

    <div class="row">
      <div class="col-xl-4 col-lg-4 col-md-4 col-sm-12 col-xs-12 text-center"
           v-for="(product, index) in products" :key="index">
        <product :product-data="product"
                 :product-index="LPTokenToPoolID(product.LPToken)"
                 :pool-enabled="product.stat"></product>
      </div>
    </div>

    <loading :active.sync="loading"
             :can-cancel="false"
             :is-full-page="true"></loading>
  </div>
</template>

<script>
import Product from "./Product";
import Loading from 'vue-loading-overlay';
import 'vue-loading-overlay/dist/vue-loading.css';
import {LPTokenToPoolID} from "@/utils/web3/constant";

export default {
  name: "dashboard",
  components: {Product, Loading},

  data() {
    return {
      allBalance: null,
      poolInfo: null,
      loading: false,

      products: [
        {
          img: "/static/icons/USDT-ETH.png",
          name: "USDT-ETH",
          txt: "Deposit USDT-ETH LP Earn HIFI",
          tx: "USDT-ETH",
          apy: "888",
          stat: true,
          dateTime: "",
          double: false,
          LPToken: "0x0d4a11d5eeaac28ec3f61d100daf4d40471f1852",
        },
        {
          img: "/static/icons/USDC-ETH.png",
          name: "USDC-ETH",
          txt: "Deposit USDC-ETH LP Earn HIFI",
          tx: "USDC-ETH",
          apy: "888",
          stat: true,
          dateTime: "",
          double: false,
          LPToken: "0xb4e16d0168e52d35cacd2c6185b44281ec28c9dc",
        },
        {
          img: "/static/icons/DAI-ETH.png",
          name: "DAI-ETH",
          txt: "Deposit DAI-ETH LP Earn HIFI",
          tx: "DAI-ETH",
          apy: "888",
          stat: true,
          dateTime: "",
          double: false,
          LPToken: "0xa478c2975ab1ea89e8196811f51a7b7ade33eb11",
        },
        {
          img: "/static/icons/COMP-ETH.png",
          name: "COMP-ETH",
          txt: "Deposit COMP-ETH LP Earn HIFI",
          tx: "COMP-ETH",
          apy: "888",
          stat: true,
          dateTime: "",
          double: false,
          LPToken: "0xcffdded873554f362ac02f8fb1f02e5ada10516f",
        },
        {
          img: "/static/icons/LEND-ETH.png",
          name: "LEND-ETH",
          txt: "Deposit LEND-ETH LP Earn HIFI",
          tx: "LEND-ETH",
          apy: "888",
          stat: true,
          dateTime: "",
          double: false,
          LPToken: "0xab3f9bf1d81ddb224a2014e98b238638824bcf20",
        },
        {
          img: "/static/icons/LAT-ETH.png",
          name: "LAT-ETH",
          txt: "Deposit LAT-ETH LP Earn HIFI",
          tx: "LAT-ETH",
          apy: "1666",
          stat: false,
          dateTime: "",
          double: true,
          LPToken: "",
        },
        {
          img: "/static/icons/LAT-CIT1.png",
          name: "LAT-CIT1",
          txt: "Deposit LAT-CIT1 LP Earn HIFI",
          tx: "LAT-CIT1",
          apy: "1888",
          stat: false,
          dateTime: "",
          double: true,
          LPToken: "",
        },
      ]
    }
  },

  methods: {
    LPTokenToPoolID: LPTokenToPoolID,
    seeTheMenu() {
      this.$router.push({name: "Dashboard"})
    },
  },
}
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
@import "../../styles/colors.scss";
@import "../../styles/fonts.scss";

.dashboard-container {
  width: 100%;
  height: 100%;

  .home-logo{
    //width: 120px;
    height: 120px;
  }

  .welcome-tit {
    margin: 0 auto 45px;
    max-width: 640px;
    font-size: 21px;
    color: $fontColor;
    letter-spacing: 2px;
    font-family: $fontTit;
  }
  .welcome-txt {
    margin-bottom: 30px !important;
    color: $txtColor;
    font-family: $fontTxt;
  }
}
</style>
