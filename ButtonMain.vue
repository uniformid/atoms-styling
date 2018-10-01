

<template>
  <div @click="clickButton" :class="this.class_button" :style="parentButton()" class="button_main_parent">
    <div class="button_main_text">{{content}}</div>
  </div>
</template>

<script>
export default {
  props: ['unique', 'content', 'class_button', 'secondary'],
  methods: {
    parentButton () {
      // #929292 = Biru = 2 || #3597FF = Abu abu = 1 || #EF4D4D = Merah = 3
      let style = {
        'min-width' : this.secondary ?  50 + 'px' : 75 + 'px',
        'height' : this.secondary ? 25 + 'px' : 30 + 'px'    
      }
      this.unique ? style['padding'] = 0 + 'px ' + 10 + 'px' : null
      return style
    },
    clickButton () {
      this.$emit('clickButton', this.content)
    }
  }
}
</script>

<style scoped>
/* How To Use */
/* <ButtonMain
  :unique="false" :content="`Edit`" :secondary="true"
  :class="'button_main_ghost'"
  @clickButton="willClickButton"></ButtonMain> */

/* button-parent */
.button_main_parent {
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 3px;
}
.button_main_text {
  font-weight: 500;
}
.button_main_parent:hover {
  cursor: pointer;
}

/* button style */
/* #3597FF = Biru = 2 || #929292 = Abu abu = 1 || #EF4D4D = Merah = 3 */
.button_main_primary {
  background-color: #3597FF;
  color: #FFFFFF;
  border: none;
}

.button_main_secondary {
  background-color: #FFFFFF;
  color: #929292;
  border: none;
}

.button_main_ghost {
  background-color: #FFFFFF;
  color: #3597FF;
  border: 1px solid #3597FF;
}

.button_main_danger {
  background-color: #EF4D4D;
  color: #FFFFFF;
  border: none;
}

</style>
