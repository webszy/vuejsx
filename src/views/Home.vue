
<template>
  
</template>


<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'home',
  components: {
    HelloWorld
  },
  data(){
    return {
      str:'test jsx',
      val:''
    }
  },
  render(h) {
    return h(
      <div>
        <p>{this.str}</p>
       <el-input value={this.val}  
       on-input={val => this.val = val} />
      </div>
      
    )
  },
}
</script>
