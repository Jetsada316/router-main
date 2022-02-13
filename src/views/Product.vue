<template>
  <div
    class="bg-image d-flex justify-content-center align-items-center"
    style="background-color: rgb(4, 40, 75)"
  >
    <v-container>
      <center><h1 style="color: white">Product</h1></center>
      <v-container class="d-flex flex-wrap">
        <v-card
          class="mx-auto mb-5"
          max-width="400"
          v-for="(i, index) in productlist"
          :key="index"
        >
          <v-img class="text-black align-end" height="350px" :src="i.imageurl">
            <v-card-title>{{ i.name }}</v-card-title>
          </v-img>

          <v-card-subtitle class="pb-0">{{ i.rightText }}</v-card-subtitle>

          <v-card-text class="text--primary">
            <div style="font-size: large">{{ i.leftText }}</div>
          </v-card-text>

          <v-card-actions>
            <v-btn color="info" text :to="'/detail/' + i.rightText"
              >detail</v-btn
            >
            <v-btn color="orange" @click="selected(i)"> Add </v-btn>
          </v-card-actions>
        </v-card>
      </v-container>

      <table class="table table-striped table-hover"></table>
      <v-container
        ><h4 class="text-danger fs-1">Total {{ total() }} Baht</h4></v-container
      >
      <v-container grid-list-xs class="white">
        <router-view :key="$route.path"></router-view>
      </v-container>
    </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      productlist: [
        {
          name: "คีย์บอร์ด Womier K66 V2 Hot Swap RGB 65% Gaming Keyboard",
          imageurl:
            "https://mercular.s3.ap-southeast-1.amazonaws.com/images/products/2021/05/womier-k66-v2-hotswap-rgb-65-keyboard-01.jpg",
          rightText:
            "มีสาย/ไร้สาย=มีสาย   ประเภทคีย์บอร์ด=Mechanical  ขนาดคีย์บอร์ด=Compact  สวิตซ์=Gateron  ประเภทสวิตซ์=Linear  เสียง=Silent  ไฟRGB=มีไฟ  สีสวิทซ์=Red",
          leftText: "Price : 2,590",
          active: false,
          price: 199,
        },

        {
          name: "คีย์บอร์ด HyperX Alloy Origins Core Gaming Keyboard",
          imageurl:
            "https://mercular.s3.ap-southeast-1.amazonaws.com/images/products/2020/03/Alloy-Origins-Core-1.jpg",
          rightText:
            "มีสาย/ไร้สาย=มีสาย   ประเภทคีย์บอร์ด=Mechanical  ขนาดคีย์บอร์ด=Tenkeyless(TKL)  สวิตซ์=HyperX  ประเภทสวิตซ์=Linear  เสียง=Silent  มาโคร=มีซอฟต์แวร์  มีไฟRGB= มีไฟสี  สวิทซ์=Blue",
          leftText: "Price : 2,890",
          active: false,
          price: 3000,
        },

        {
          name: "คีย์บอร์ด Akko 3068 Silent White Backlit Wireless Keyboard Akko Switch",
          imageurl:
            "https://mercular.s3.ap-southeast-1.amazonaws.com/images/products/2021/06/Akko/AKKO_3068_White_1.jpg",
          rightText:
            "มีสาย/ไร้สาย=มีสาย   ประเภทคีย์บอร์ด=Mechanical    สวิตซ์=Akko Switch  ประเภทสวิตซ์=Akko Switch  เสียง=Silent  มาโคร=มีซอฟต์แวร์  มีไฟRGB=มีไฟ สีสวิทซ์=Red",
          leftText: "Price : 2,190",
          active: false,
          price: 25,
        },

        {
          name: "คีย์บอร์ด Ducky One 2 Rosa Special Edition Cow Mechanical Keyboard",
          imageurl:
            "https://mercular.s3.ap-southeast-1.amazonaws.com/images/products/2022/01/Product/ducky-one-2-rosa-special-edition-cow-mechanical-keyboard-brown-switch-01.jpg",
          rightText:
            "มีสาย/ไร้สาย=มีสาย  ประเภทคีย์บอร์ด=Mechanical  ขนาดคีย์บอร์ด=Full-Size  สวิตซ์=Cherry  ประเภทสวิตซ์=Tactile,Linear  เสียง=Clicky,Silent  สีสวิทซ์=Brown,Red,Blue  วัสดุคีย์แคป=PBT",
          leftText: "Price : 3,990",
          active: false,
          price: 99,
        },
        {
          name: "คีย์บอร์ดไร้สาย IQUNIX F96 Avocado Wireless Mechanical Keyboard (EN)",
          imageurl:
            "https://mercular.s3.ap-southeast-1.amazonaws.com/images/products/2021/08/Product/iqunix-f96-avocado-wireless-mechanical-keyboard-en-01.jpg",
          rightText:
            "มีสาย/ไร้สาย=ไร้สาย  ประเภทคีย์บอร์ด=Mechanical  ขนาดคีย์บอร์ด=96%  สวิตซ์=Cherry  ประเภทสวิตซ์=Linear  เสียง=Silent  สีสวิทซ์=Silent Red  วัสดุคีย์แคป=PBT",
          leftText: "Price : 9,590",
          active: false,
          price: 99,
        },
        {
          name: "คีย์บอร์ด SteelSeries Apex 3 RGB Gaming Keyboard",
          imageurl:
            "https://mercular.s3.ap-southeast-1.amazonaws.com/images/products/2020/01/APEX-3-1.jpg",
          rightText:
            "มีสาย/ไร้สาย=มีสาย  ประเภทคีย์บอร์ด=Membrane  ขนาดคีย์บอร์ด=Full-Size  สวิตซ์=SteelSeries    เสียง=Silent มาโคร=มีซอฟต์แวร์  มีไฟRGB= มีไฟ  ",
          leftText: "Price : 2,150",
          active: false,
          price: 19500,
        },
        {
          name: "คีย์บอร์ด Loga Yaksa PRO Printstream TKL Mechanical Keyboard",
          imageurl:
            "https://mercular.s3.ap-southeast-1.amazonaws.com/images/products/2021/11/Product/loga-yaksa-pro-printstream-tkl-mechanical-keyboard-en-01.jpg",
          rightText:
            "มีสาย/ไร้สาย=มีสาย  ประเภทคีย์บอร์ด=Mechanical  ขนาดคีย์บอร์ด=Tenkeyless (TKL)  สวิตซ์=Gateron    เสียง=Silent   มีไฟRGB= มีไฟ",
          leftText: "Price : 3,490",
          active: false,
          price: 25590,
        },
        {
          name: "คีย์บอร์ด Keychron K8 Hot-swappable Wireless Mechanical Keyboard (TH/EN)",
          imageurl:
            "https://mercular.s3.ap-southeast-1.amazonaws.com/images/products/2021/10/Product/keychron-k8-hot-swappable-wireless-mechanical-keyboard-th-en-light-grey-red-switch-01.jpg",
          rightText:
            "มีสาย/ไร้สาย=มีสาย/ไร้สาย   ประเภทคีย์บอร์ด=Mechanical  ขนาดคีย์บอร์ด=Tenkeyless (TKL)  สวิตซ์=Gateron  ประเภทสวิตซ์=Tactile, Linear  เสียง=Clicky, Silent  ไฟRGB=มีไฟ  สีสวิทซ์=Blue, Brown, Red",
          leftText: "Price : 4,090",
          active: false,
          price: 62900,
        },
      ],
    };
  },
  methods: {
    selected: function (i) {
      i.active = !i.active;
    },
    total: function () {
      var sum = 0;
      this.productlist.forEach(function (i) {
        if (i.active) {
          sum += i.price;
        }
      });
      return sum;
    },
  },
};
</script>

<style>
h2 {
  color: white;
}
</style>
