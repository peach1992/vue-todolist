<template>
  <div class="todo">
       <input class="input" v-model="value" placeholder="输入要做的事情" v-on:keyup.enter="submit">
       <button class="btna" v-on:click="submit">enter</button>
       <table border="1">
            <tr><th class="first">序号</th><th>做什么</th><th>创建时间</th><th>完成情况</th></tr>
           <tr v-for="(item,index) in textlist"><td class="first">{{index+1}}</td> <td v-bind:class="{done:item.done}">{{item.text}}</td> <td>
           {{item.time.year}}/{{item.time.month}}/{{item.time.day}}</td><td>
           <button v-on:click="item.done=true" class="btnb">完成了</button>
           <button v-on:click="textlist.splice(index,1)" class="btnb"> 删除 </button></td>
           </tr>
       </table>
  </div>
</template>

<script>
export default {
  name: 'todo',
  data () {
    return {
      value: "",
      textlist:[
      {text:"coding",time:{year:2017,month:1,day:1},done:false},{text:"fishing",time:{year:2017,month:1,day:1},done:false}
      ]
    }
  },
  methods:{
    submit:function(){
    this.textlist.push({text:this.value,time:{year:new Date().getFullYear(),month:new Date().getMonth()+1,day:new Date().getDate()},done:false})
    }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
     .todo{
        padding:10px;
        width:40%;
        height:auto;
        border:1px solid #eee;
        margin:10% auto;
        background:#e8e8e8;
     }
     table{
		width:100%;
		table-layout:fixed; 
		empty-cells:show; 
		border-collapse: collapse; 
		margin:0 auto; 
     }
	td{ 
	height:30px; 
	} 
	.done{
	text-decoration:line-through;
	}
	table th { 
		background-repeat:repeat-x; 
		height:30px; 
    } 
	table td,table th{ 
		border:1px solid #cad9ea; 
		padding:0 1em 0; 
    } 
    .first{
    width:40px;
    text-align:center;
    }
     .input{ 
        width:50%;
        height:30px;
        float:left;
        margin:10px 30px;
     }
     .btna{
      margin:10px 20px;
      height:35px;
      width:50px;
     }
     li{
     padding:5px 0;
     }
     .btnb{
         display: table-cell;
    vertical-align: middle;
      height:25px ;
      width:100%;
      background:#26B1B6;
     }
</style>
