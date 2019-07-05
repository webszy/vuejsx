
<script>

export default {
name:'test',
components:{},
data(){
return {
  arr:[1,2,3,4,5,6]
  }
 },
 render(h) {
   return (
     <ul>
        {this.arr.map(item=>{return (<li>{item}</li>)})}
      </ul>
   )
 },
}
</script>
<style>


</style>
