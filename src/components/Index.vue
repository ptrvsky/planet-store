<template>
  <div class="index">
    <div class="stars small"></div>
    <div class="stars medium"></div>
    <div class="stars big"></div>
    <GeneralContent></GeneralContent>
  </div>
</template>

<script>
import GeneralContent from "@/components/index/GeneralContent";
export default {
  name: 'Index',
  components: {
    GeneralContent,
  },
}
</script>

<style scoped lang="scss">
@function generate-stars($amount_of_stars) {
  $stars: '#{random(2100)}px #{random(2100)}px #FFF';
  @for $i from 1 through $amount_of_stars {
    $stars: '#{$stars}, #{random(4000)}px #{random(4000)}px #FFF'
  }
  @return unquote($stars);
}

@keyframes moveStars {
  from {
    transform: translateX(0);
  } to {
    transform: translateX(-2000px);
  }
}

.index {
  background-color: #02090e;
  min-height: 100vh;
  min-width: 100%;

  .stars {
    position: absolute;
    top: 0;
    left: 0;

    &.small {
      width: 1px;
      height: 1px;
      box-shadow: generate-stars(1500);
      animation: moveStars 50s linear infinite;
    }

    &.medium {
      width: 2px;
      height: 2px;
      box-shadow: generate-stars(500);
      animation: moveStars 100s linear infinite;
    }

    &.big {
      width: 3px;
      height: 3px;
      box-shadow: generate-stars(200);
      animation: moveStars 150s linear infinite;
    }
  }
}
</style>
