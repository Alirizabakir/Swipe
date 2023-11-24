<template>
  <!--begin::App-->
  <div class='d-flex flex-column flex-root app-root' id='kt_app_root'>
    <!--begin::Page-->
    <div class='app-page flex-column justify-content-between vh-100' id='kt_app_page'>
      <div class='d-flex align-items-center col-11 col-xl-9 mx-auto'>
        <!--begin::Wrapper-->
        <figure class='border-bottom border-warning w-100 py-8 py-lg-8 mt-4 mt-lg-0 border-opacity-25'>
          <img class='col-3 col-sm-2 col-md-2 col-lg-1' src='/public/media/svg/shapes/swipe-t.png' alt='mascot'>
        </figure>
        <!--end::Wrapper-->
      </div>
      <div class='flex-grow-1 position-relative overflow-hidden'>
        <div class='col-11 col-xl-9 mx-auto h-100'>
          <!--begin::Wrapper-->
          <figure class='w-100 h-100 position-fixed top-0 z-2 d-flex align-items-center justify-content-center'
                  style='right: 0'>
            <img src='/public/media/svg/shapes/swipe-bg.png' alt='' class='col-10'>
          </figure>
          <!--end::Wrapper-->

          <!--begin::Wrapper-->
          <div
            class='position-relative d-flex flex-column align-items-center align-items-lg-start justify-content-start justify-content-lg-center h-75'
            style='z-index: 100'>
            <div class='d-flex align-items-end mb-4 col-12 justify-content-lg-start justify-content-center'
                 style='height: 70px'>
              <p class='m-0  fw-bolder display-0 text-nowrap font-tamil fw-bold text-gray-900'>Time to Social</p>
              <img class='col-5 col-md-4  col-xxl-4 pb-1 pb-md-2 pb-lg-2' src='/public/media/svg/shapes/blast.png' alt=''>
            </div>
            <p class='font-tamil d-none d-xl-block display-6 fw-semibold ps-4 text-dark opacity-50 mb-10'
               style='letter-spacing: 5px'>Swipe is a Socialfi project that will exist on the Blast</p>
            <p class='font-tamil d-none d-md-block d-xl-none fs-2 fw-semibold ps-4 text-dark opacity-50 mb-10'
               style='letter-spacing: 2px'>Swipe is a Socialfi project that will exist on the Blast</p>
            <p class='font-tamil d-block d-md-none text-dark opacity-50 text-center mb-8'>Swipe is a Socialfi project
              that
              will exist on the Blast</p>
            <div
              class='border border-warning rounded-pill overflow-hidden d-flex align-items-center col-12 col-md-6 ms-0 ms-md-4'>
              <label for='email' class='flex-grow-1 h-100'>
                <input id='email' type='email' placeholder='Email'
                       class='form-control border-0 fs-2 text-warning px-10 bg-gradient h-100 d-block'>
              </label>
              <button
                style='filter: drop-shadow(0 0 3px #ffdd00)'
                class='btn bg-warning rounded-pill p-6 px-6 fs-5 px-lg-12 text-light-dark fw-bolder fs-2 text-nowrap bg-hover-opacity-50 pointer-event'>
                Notify Me
              </button>
            </div>
          </div>
          <!--end::Wrapper-->

        </div>

        <!--begin::Wrapper-->
        <div class='position-absolute top-0 d-flex align-items-end mb-20 mt-10 mt-lg-0 z-1 user-select-none'
             style='right: 0; opacity: .25'>
          <img class='mascot user-select-none col-9 col-xl-10 col-xl-11' src='/public/media/svg/shapes/swipe.png'
               alt='mascot'>
        </div>
        <!--end::Wrapper-->
      </div>
    </div>
    <!--end::Page-->
  </div>
  <!--end::App-->

  <KTScrollTop />
</template>

<script lang='ts'>
import { defineComponent, nextTick, onBeforeMount, onMounted, watch } from 'vue'
import KTScrollTop from '@/layouts/main-layout/extras/ScrollTop.vue'
import { useRoute } from 'vue-router'
import { reinitializeComponents } from '@/core/plugins/keenthemes'
import LayoutService from '@/core/services/LayoutService'
import SVG from '@/core/helpers/kt-icon/SVG.vue'
import { getAssetPath } from '@/core/helpers/assets'

export default defineComponent({
  name: 'default-layout',
  methods: { getAssetPath },
  components: {
    SVG,
    KTScrollTop
  },
  setup() {
    const route = useRoute()

    onBeforeMount(() => {
      LayoutService.init()
    })

    onMounted(() => {
      nextTick(() => {
        reinitializeComponents()
      })
    })

    watch(
      () => route.path,
      () => {
        nextTick(() => {
          reinitializeComponents()
        })
      }
    )
  }
})
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Bakbak+One&display=swap');
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@100;200;300;400;500;600;700;800;900&display=swap");

.bg-gradient {
  background: linear-gradient(90deg, rgba(255, 209, 0, .13) 0%, rgba(255, 209, 0, .05) 40%, rgba(249, 255, 4, 0) 100%) !important;
}
.bg-gradient::placeholder {
  color: #fff200;
  opacity: 1; /* Firefox */
}

.font-tamil {
  font-family: 'Bakbak One', sans-serif;
  }

.font-montserrat {
  font-family: 'Bakbak One', sans-serif;
}

.mascot {
  transform: translateX(59%);
}

@media screen and (min-width: 1200px) {
  .mascot {
    transform: translateX(36%);
  }
}

@media screen and (min-width: 1400px) {
  .mascot {
    transform: translateX(35%);
  }
}
</style>
