<template>
    <el-card style="margin:30px">
      <h2 style="margin:10px"><svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" viewBox="0 0 16 16">
			<path d="M13 2.5a1.5 1.5 0 0 1 3 0v11a1.5 1.5 0 0 1-3 0v-.214c-2.162-1.241-4.49-1.843-6.912-2.083l.405 2.712A1 1 0 0 1 5.51 15.1h-.548a1 1 0 0 1-.916-.599l-1.85-3.49a68.14 68.14 0 0 0-.202-.003A2.014 2.014 0 0 1 0 9V7a2.02 2.02 0 0 1 1.992-2.013 74.663 74.663 0 0 0 2.483-.075c3.043-.154 6.148-.849 8.525-2.199V2.5zm1 0v11a.5.5 0 0 0 1 0v-11a.5.5 0 0 0-1 0zm-1 1.35c-2.344 1.205-5.209 1.842-8 2.033v4.233c.18.01.359.022.537.036 2.568.189 5.093.744 7.463 1.993V3.85zm-9 6.215v-4.13a95.09 95.09 0 0 1-1.992.052A1.02 1.02 0 0 0 1 7v2c0 .55.448 1.002 1.006 1.009A60.49 60.49 0 0 1 4 10.065zm-.657.975 1.609 3.037.01.024h.548l-.002-.014-.443-2.966a68.019 68.019 0 0 0-1.722-.082z"/>			</svg>  TTS 文本朗读</h2>
      <el-input v-model="ta" :rows="8" type="textarea" style="width: 80%;margin:20px" placeholder="朗读内容....."/><br>
      <el-button style="margin:20px" @click="go" bg text>生成</el-button><br>
      <audio controls :src="isv" style="margin:20px;width: 80%;"></audio><br>
      <br><br>
     
    </el-card>
    <div>
  <h3 style="text-align: center;">网站浏览次数</h3><br>
  <div style="text-align: center; width:100%;height:100%; display: table;">
   <span style="display: table-cell; vertical-align: middle; ">
    <img style="margin:0 auto" src="https://api.vore.top/api/ACGcount?code=toolstack">
   </span>
</div>
 </div>
</template>
<script setup>
import  { ref } from 'vue'
const ta=ref('')
const isv=ref('')
function go(){
    
    fetch(`https://api.vore.top/api/TTS?text=`+ta.value).
         then((res) => res.json()
         .then((data1) => {
          const{data:{download,info}}=data1;
          isv.value="https"+download.slice(4);
          if(info=="生成成功"){
            ElMessage({
                message: info,
                type: 'success',
                 })
          }else{
            ElMessage.error(info)
          }
         })
      )
}

</script>