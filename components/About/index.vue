<template>
  <div class="about">
    <div class="about__line">
      <div class="about__slider f-carousel f-carousel--about " id="aboutSlider">
        <div class="f-carousel__viewport">
          <div class="f-carousel__track">
            <div class="about__item f-carousel__slide" v-for="index in slidesNumber">
              <NuxtPicture class="slider-about__image" :src="`/img/slider/about/slide-${index + 1}.jpg`"
                           :alt="`Фото автоцентра ${settings.dealer_name} в г. ${settings.contact_address}`"
                           :width="864"
                           :height="468"/>
            </div>
          </div>
        </div>
      </div>
      <div class="about__text">
        <p class="text__p">
          {{ settings.dealer_name }} — автоцентр новых автомобилей в {{ settings.contact_in_city }}. У нас лучшие
          условия
          по автокредитованию, низкая ставка, возможность приобретения нового авто
          в кредит без первого взноса. Мы предлагаем вашему вниманию более 35
          брендов ведущих автомобильных концернов.
        </p>
        <p class="text__p">
          Благодаря сотрудничеству с
          крупнейшими банками и статусу официального дилера клиенты нашего
          автоцентра получают возможность оформления автокредита на новый
          автомобиль не выходя из салона. Каждому, кто приобретает авто в {{ settings.dealer_name }}, мы дарим ценные
          подарки и
          предлагаем лучшие условия в {{ settings.contact_in_city }}.
        </p>
        <p class="text__p">
          Мы наполняем автопарк за счет прямых поставок из Европы и Китая. Налаженная сеть партнеров в Поднебесной
          обеспечивает наличие всех актуальных новинок.
        </p>
        <p class="text__p">
          Наш автоцентр удобно расположен в 3 минутах ходьбы от метро Аннино, на юге Москвы, в самом сердце мира
          столичных автопродаж. Приезжайте и убедитесь сами — у нас обширная площадка новых автомобилей в наличии,
          новейшая клиентская зона, кредитные специалисты и масса положительных впечатлений от покупки долгожданного
          авто.
        </p>
      </div>
    </div>
    <client-only>
      <div class="about__panorama" style="position:relative;overflow:hidden;"><a
          href="https://yandex.ru/maps/org/atlas_auto/161638344849/?utm_medium=mapframe&utm_source=maps"
          style="color:#eee;font-size:12px;position:absolute;top:0px;">Atlas Auto</a><a
          href="https://yandex.ru/maps/213/moscow/category/car_dealership/184105322/?utm_medium=mapframe&utm_source=maps"
          style="color:#eee;font-size:12px;position:absolute;top:14px;">Автосалон в Москве</a>
        <iframe
            src="https://yandex.ru/map-widget/v1/org/atlas_auto/161638344849/?l=stv%2Csta&ll=37.590196%2C55.581213&panorama%5Bdirection%5D=298.271431%2C24.233658&panorama%5Bfull%5D=true&panorama%5Bpoint%5D=37.590127%2C55.581050&panorama%5Bspan%5D=114.063749%2C60.000000&utm_source=share&z=18"
            frameborder="1" allowfullscreen="true" style="position:relative;"></iframe>
      </div>
    </client-only>
  </div>
</template>

<script setup lang="ts">
import {useSiteConfig} from "~/store/siteConfig";
import {Carousel} from "@fancyapps/ui";

const settings = useSiteConfig().settings
const slidesNumber = 20;
let slider: Carousel
const initSlider = () => {
  const container = document.getElementById("aboutSlider");
  const options = {
    infinite: true,
    center: false,
    transition: 'slide',
    getProgress: 'center',
    Thumbs: {
      type: "modern",
    },
  };
  slider = new Carousel(container, options);
}

onMounted(() => {
  initSlider()
})
</script>
