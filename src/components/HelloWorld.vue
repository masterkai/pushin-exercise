<template>
    <div>
        <img src="../assets/pigP.gif" ref="pig" class="pig"/>
        <div class="container" id="demo">
            <img src="../assets/0_Horse.png" ref="Horse" class="Horse"/>
            <img src="../assets/0_Rabbit.png" ref="Rabbit" class="Rabbit"/>
            <img src="../assets/0_Cow.png" ref="Cow" class="Cow"/>
            <img src="../assets/0_Sheep.png" ref="Sheep" class="Sheep"/>
        </div>
        <img src="../assets/風車.gif" class="windmill"/>
        <img src="../assets/大標.png" class="Subject"/>
        <div class="btn"></div>


    </div>
</template>

<script>
  import {TimelineMax, TweenMax, Power2} from 'gsap'

  export default {
    mounted() {
      const windowWidth = window.innerWidth
      const {pig} = this.$refs

      const timeline = new TimelineMax()
      timeline.set(pig, {y: '+=10', x: '-=50', autoAlpha: 0})
// set pig's opacity to 0
      timeline.to(pig, 0, {autoAlpha: 1})

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
    }
  }
</script>

<style>
    @keyframes initial {
        to {
            transform: rotate3d(0, 0, 1, 0deg);
        }
    }

    @keyframes swing {
        20% {
            transform: rotate3d(0, 0, 1, 10deg);
        }

        40% {
            transform: rotate3d(0, 0, 1, -10deg);
        }

        60% {
            transform: rotate3d(0, 0, 1, 10deg);
        }

        80% {
            transform: rotate3d(0, 0, 1, -10deg);
        }

        to {
            transform: rotate3d(0, 0, 1, 0deg);
        }
    }

    .container {
        margin: 0 auto;
        max-width: 1660px;
        position: relative;
    }

    .Subject {
        position: absolute;
        left: 50%;
        transform: translateX(-50%);
        z-index: 11;
    }

    .btn {
        cursor: pointer;
        background-image: url("../assets/BT_P.png");
        width: 418px;
        height: 126px;
        background-repeat: no-repeat;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translateX(-50%);
        z-index: 11;
    }

    .btn:hover {
        background-image: url("../assets/BT_R.png");
    }

    .Horse {
        cursor: pointer;
        position: absolute;
        top: 790px;
        left: 50px;
        animation: swing 4s infinite ease-in-out;
    }

    .Horse:hover {
        animation: initial;
    }

    .Rabbit {
        cursor: pointer;
        position: absolute;
        top: 768px;
        left: 526px;
        transform-origin: 60% 50%;
        animation: swing 4s infinite ease-in-out;
        animation-delay: .5s;
    }

    .Rabbit:hover {
        animation: initial;
    }

    .Cow {
        cursor: pointer;
        position: absolute;
        top: 800px;
        right: 430px;
        animation: swing 4s infinite ease-in-out;
        animation-delay: .25s;
    }

    .Cow:hover {
        animation: initial;
    }

    .Sheep {
        cursor: pointer;
        position: absolute;
        top: 830px;
        right: 50px;
        animation: swing 4s infinite ease-in-out;
        animation-delay: 1s;
    }

    .Sheep:hover {
        animation: initial;
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