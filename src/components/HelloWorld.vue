<template>
    <div>
        <img src="../assets/pigP.gif" ref="pig" class="pig"/>
        <img src="../assets/0_Horse.png" ref="Horse" class="Horse"/>
        <img src="../assets/0_Rabbit.png" ref="Rabbit" class="Rabbit"/>
        <img src="../assets/0_Cow.png" ref="Cow" class="Cow"/>
        <img src="../assets/0_Sheep.png" ref="Sheep" class="Sheep"/>
        <img src="../assets/風車.gif" class="windmill"/>
        <img src="../assets/大標.png" class="Subject"/>

    </div>
</template>

<script>
  import {TimelineMax, TweenMax, Power2} from 'gsap'

  export default {
    mounted() {
      const windowWidth = window.innerWidth
      const {pig, Horse, Rabbit, Cow, Sheep} = this.$refs

      const timeline = new TimelineMax()
      timeline.set(pig, {y: '+=10', x: '-=50', autoAlpha: 0})
      timeline.set(Horse, {y: '+=10', autoAlpha: 0})
      timeline.set(Rabbit, {y: '+=10', autoAlpha: 0})
      timeline.set(Cow, {y: '+=10', autoAlpha: 0})
      timeline.to(pig, 0, {autoAlpha: 1})

      timeline.set(Sheep, {y: '+=10', autoAlpha: 0})
      timeline.to(Horse, 0, {autoAlpha: 1, rotation: -5})
      timeline.to(Rabbit, 0, {autoAlpha: 1})
      timeline.to(Cow, 0, {autoAlpha: 1, rotation: 5})

      timeline.to(Sheep, 0, {autoAlpha: 1, rotation: -5})


      TweenMax.to(pig, .25, {
        css: {y: -50, transformOrigin: '50% 50%'},// remove default easing for seamless loop
        repeatDelay: null,
        repeat: -1,
        yoyo: true,
        ease: Power2.ease
      })
      timeline.to(pig, 5, {
          css: {x: windowWidth, transformOrigin: '50% 50%'},// remove default easing for seamless loop
          repeatDelay: null,
          repeat: -1,
          yoyo: false
        }
      )

      timeline.to(Horse, 1, {
        css: {rotation: 5, transformOrigin: '50% 50%'},// remove default easing for seamless loop
        repeatDelay: null,
        repeat: -1,
        yoyo: true,
        ease: Power2.easeInOut
      })

      timeline.to(Rabbit, .5, {
        css: {y: -6, transformOrigin: '50% 50%'},// remove default easing for seamless loop
        repeatDelay: null,
        repeat: -1,
        yoyo: true,
        ease: Power2.easeIn
      })

      timeline.to(Sheep, 1, {
        css: {rotation: 5, transformOrigin: '50% 50%'},// remove default easing for seamless loop
        repeatDelay: null,
        repeat: -1,
        yoyo: true,
        ease: Power2.easeInOut
      })

      timeline.to(Cow, 1, {
        css: {rotation: -5, transformOrigin: '50% 50%'},// remove default easing for seamless loop
        repeatDelay: null,
        repeat: -1,
        yoyo: true,
        ease: Power2.easeInOut
      })


    }
  }
</script>

<style>
    .Subject {
        position: absolute;
        left: 50%;
        transform: translateX(-50%);
        z-index: 11;
    }

    .Horse {
        position: absolute;
        top: 790px;
        left: 50px;
    }

    .Rabbit {
        position: absolute;
        top: 768px;
        left: 526px;
    }

    .Cow {
        position: absolute;
        top: 800px;
        right: 430px;
    }

    .Sheep {
        position: absolute;
        top: 830px;
        right: 50px;
    }

    .pig {
        position: absolute;
        top: 600px;
        /*display: none;*/
        height: auto;
        max-width: 100%;
        z-index: 10;
    }

    .windmill {
        position: absolute;
        top: 0;
    }


</style>