<template>
  <div class="box">
    <el-input placeholder="请输入搜索内容" v-model="searchText"  @keyup.enter.native="search" class="input-with-select"   >
      <el-select slot="prepend" v-model="searchEngine" placeholder="搜索引擎" >
        <el-option
            v-for="item in options"
            :key="item.value"
            :label="item.label"
            :value="item.value"
        >
          <svg class="icon" aria-hidden="true">
            <use :xlink:href="item.icon"></use>
          </svg>
          <span>{{item.label}}</span>
        </el-option>
      </el-select>
      <el-button  slot="append" icon="el-icon-search" type="primary"  @click="search" style="width:5rem;">搜索</el-button>
    </el-input>


  </div>
</template>
<script>
export default {
  name: 'MainSearch',
  methods:{
    search(){
      switch (this.searchEngine){
        case "baidu":
          window.open(`https://www.baidu.com/s?wd=${this.searchText}`)
          break;
        case "google":
          window.open(`https://www.google.com/search?q=${this.searchText}`)
          break;
        case "bing":
          window.open(`https://cn.bing.com/search?q=${this.searchText}`)
          break;
      }
      let url = `https://www.baidu.com/s?wd=${this.searchText}`;
      window.open(url);
    }
  },
  data(){
    return {
      searchText:"",
      searchEngine:"bing",
      options: [{
        value: 'baidu',
        label: '百度',
        icon: "#icon-Group"
      },
      {
        value: 'google',
        label: '谷歌',
        icon: "#icon-guge"
      },
      {
        value: 'bing',
        label: '必应',
        icon: "#icon-biying"
      },
      ]
    }
  }
}
</script>
<style lang="less" scoped>
.box{
  display: flex;
  justify-content: center;
  align-content: center;
}
.el-input{
  width: 40rem;
}
.el-select{
 width: 7rem;
}

.el-select-dropdown__item{
  display: flex;
  justify-content: center;
  align-content: center;
}
.icon{
  width: 2rem;
  height: 2rem;
}


.input-with-select /deep/.el-input-group__append,.input-with-select /deep/.el-input-group__prepend {
  background-color: deepskyblue;
  color:white;
  border:0px;
}
/deep/.el-input__inner {
  background-color: rgba(255, 255, 255, 0.3); /* 半透明背景 */
  backdrop-filter:blur(10px); /* 应用毛玻璃效果 */
  -webkit-backdrop-filter:blur(10px); /* Safari 和 Chrome 的前缀 */
  border:0;
  border-radius: 0px;
  color:white;
}



</style>