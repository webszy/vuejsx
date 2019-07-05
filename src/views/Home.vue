

<script>
// @ is an alias to /src
import test from './a'
export default {
  name: 'home',
  components: {
    test
  },
  data() {
    return {
      str:'VueJSX',
      inputValues:'这是一个文本框',
      arr:[1,2,3,4,5,6]
    }
  },
  render(h) {
    return (
      <div>
        <h1>{this.str}</h1>
        <el-input value={this.inputValues} 
        on-input={val=>{this.inputValues=val}}/>
        <el-button on-click={()=>this.$message.warning('hellworld')}>测试alert</el-button>
        <el-button on-click={this.showMsg}>测试message的虚拟dom</el-button>
        <ul>
        {this.arr.map(item=>{return (<li>{item}</li>)})}
        </ul>
      </div>
    )
  },
  methods: {
    showMsg(){
      // const h = this.$createElement;
      // {arr.map(item=>{return (<li>{item}</li>)})}
      const vnode=(()=>{
        return this.$createElement(
          <ul>
            <li>1</li>
          </ul>
        )
      })()
      this.$msgbox({
          title: '消息',
          message: vnode,
          showCancelButton: true,
          confirmButtonText: '确定',
          cancelButtonText: '取消',
          dangerouslyUseHTMLString:true,
           beforeClose: (action, instance, done) => {
            if (action === 'confirm') {
              instance.confirmButtonLoading = true;
              instance.confirmButtonText = '执行中...';
              setTimeout(() => {
                done();
                setTimeout(() => {
                  instance.confirmButtonLoading = false;
                }, 300);
              }, 3000);
            } else {
              done();
            }
          }
        }).then(action => {
          this.$message({
            type: 'info',
            message: 'action: ' + action
          });
        });
    }
  },
}
</script>
