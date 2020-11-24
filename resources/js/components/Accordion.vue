<template>
  <div class="accordion">
    <!-- <div class="header" :class="{ 'accordion-showing': show, 'accordion-hiding': leaving }" @click="toggle">
      <slot name="header">HINT</slot>      
    </div> -->
    
    <div class="body" :class="{ 'accordion-showing': show }">
      <div class="grid grid-cols-8 gap-8">
        <div class="col-span-5 content">
          <h3 @click="toggle" class="cursor-pointer">Single Oven</h3>
          <expandable>
            <div v-show="show" class="expandable">
              <p>Probabo, inquit, modo dixi, constuto, ut enim ipsam pr se esse ratione neque porro quisquam est, quid aut interrogari ut placet, inquam tum dicere exorsus est laborum et negent satis esse, ut ita ruant itaque earum rerum facilis est.</p>
              <button>Learn more</button>
            </div>
          </expandable>
        </div>
        <div class="col-span-1 expandable"></div>
        <expandable>
          <div v-show="show" class="col-span-2 expandable">
            <img src="/images/single-oven.jpg" width="100%" height="auto" />
          </div>
        </expandable>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  

  data () {
    return {
      show: false,
      leaving: false,
    }
  },

  // computed: {
  //   show: {
  //     get () {
  //       return this.value
  //     },

  //     set (value) {
  //       this.$emit('input', value)
  //     },
  //   }
  // },
  
  methods: {
    toggle () {
      this.show = ! this.show
    },
    // enter (el, done) {
    //   $(el).slideDown(150, done)
    // },
    // leave (el, done) {
    //   $(el).slideUp(150, done)
    // },
    beforeEnter (el) {
      el.style.height = '0'
    },
    enter (el) {
      el.style.height = el.scrollHeight + 'px'
    },
    beforeLeave (el) {
      el.style.height = el.scrollHeight + 'px'
      this.leaving = true
    },
    afterLeaving () {
      this.leaving = false
    },
    leave (el) {
      el.style.height = '0'
    }
  }
}
</script>
