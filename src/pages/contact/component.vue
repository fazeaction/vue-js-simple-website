//
// component.vue

//
// AUTHOR
//
// Developed by Christian MacMillan in 2016
// https://github.com/cmacmillanmarin
// hello@christian-macmillan.com
//

<template>

    <div class="page contact">

        <p v-el:txt>Contact</p>

    </div>

</template>

<script>

import Vue from 'vue'
import transition from '../../config/transitions'
import emitter from '../../../local_modules/events'

export default Vue.extend({

    ready() {

        emitter.on(emitter.events.transitionIn, this.transitionIn)
        emitter.on(emitter.events.transitionOut, this.transitionOut)

    },

    methods : {

        transitionIn() {

            transition.setTransitionInDuration(500)
            TweenMax.to(this.$el, 0.5, { opacity : 1 })
            TweenMax.from(this.$el, 0.5, { y : 100 })
            TweenMax.from(this.$els.txt, 0.5, { scale : 0.25, rotation: 360 })

        },

        transitionOut() {

            transition.setTransitionOutDuration(500)
            TweenMax.to(this.$el, 0.5, { y : 100, opacity: 0 })

        }

    },

    destroyed() {

        emitter.removeListener(emitter.events.transitionIn, this.transitionIn)
        emitter.removeListener(emitter.events.transitionOut, this.transitionOut)

    }

})

</script>
