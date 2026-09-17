<template>
  <!-- 写网页标签的地方 -->
  <div class="about">
    {{ strMsg }}
    <h1 v-html="strMsg"></h1>
    <div v-text="strHTML"></div>
    <div v-html="strHTML"></div>
    <input type="text" :value="strMsg"><br />
    <hr />
    <button @click="my_init">初始化数据</button>
    性别：<input type="text" id="txtSex" value=""><button @click="fun02">查询</button>
  <table border="1">
    <thead>
      <tr><th>学号</th><th>姓名</th><th>年龄</th><th>性别</th><th>操作</th></tr>
    </thead>
    <tbody>
      <tr v-for="(item,index) in stusTemp" :key="index">
        <td>{{ item.stuNo }}</td>
        <td>{{ item.stuName }}</td>
        <td>{{ item.stuAge }}</td>
        <td>{{ item.stuSex }}</td>
        <td><button>查看</button> &nbsp;&nbsp;<button>修改</button> &nbsp;&nbsp;<button>删除</button></td>

      </tr>      
    </tbody>
    <tfoot>

    </tfoot>
  </table>
    <hr />
    <table v-show="isExist"  class="my-center">
            <thead>
                <tr><th>月份</th><th>工资</th><th>奖金</th><th>小费</th><th>支出</th></tr>
            </thead>
            <tbody>
                <tr>
                    <td>一月</td>
                    <td>5000</td>
                    <td>1000</td>
                    <td>500</td>
                    <td>4000</td>
                </tr>
                <tr><td>二月</td><td>5000</td><td>1500</td><td>10</td><td>6000</td></tr>
                <tr><td>三月</td><td>5000</td><td>800</td><td>200</td><td>8000</td></tr>
            </tbody>
            <tfoot>
                <tr><td>合计</td><td>15000</td><td>3300</td><td>710</td><td>18000</td></tr>
            </tfoot>
        </table><br />
        <button @click="fun01">测试</button>
  </div>
  <div v-if="score >= 60">
    及格
  </div>
  <div v-else>
    不及格
  </div>
  <hr />
  <div v-if="score >= 90">
    A
  </div>
  <div v-if="score >= 80 && score <= 89">
    B
  </div>
  <div v-else>
    不及格
  </div>
  <hr />
  <ul>
    <li v-for="(v,index) in scores" :key="index">{{ index }}:{{ v }}</li>
  </ul>
  <hr />
  <ul>
    <li v-for="(v,k,index) in stu">{{ index }}:{{ v }}</li>
  </ul>
  <hr />
  <ul>
    <li v-for="(item,index) in stus" :key="index">{{ index }}:{{ item.stuNo }}</li>
  </ul>

  

</template>
<script lang="ts" setup>
// js 或者 ts代码的地方
import {Student} from '@/entity/Entity'
import {ref} from 'vue'
const strHTML:string="<font color='red'>你好</font>"
const strMsg:string="你好！我刚开始学习Vue" //常量不能修改
const isExist:boolean = true 
const score:number = 80
const scores:number[] = [45,6,78,21,45,7,456,78,39]
//const scores:Array<number> = [45,6,78,21,45,7,456,78,39]

const stu:Student={
  "stuNo":"stu001",
  "stuName":"张三",
  "stuAge":20,
  "stuAddress":"新乡",
  "stuSex":"M"
}
const stus:Student[]=[
  {stuNo:'stu001',stuAge:18,stuName:'zhangsan',stuAddress:'xinxiang',"stuSex":"M"},
  {stuNo:'stu002',stuAge:20,stuName:'zhangsan',stuAddress:'xinxiang',"stuSex":"F"},
  {stuNo:'stu003',stuAge:25,stuName:'zhangsan',stuAddress:'xinxiang',"stuSex":"M"},
  {stuNo:'stu004',stuAge:16,stuName:'zhangsan',stuAddress:'xinxiang',"stuSex":"F"},
  {stuNo:'stu005',stuAge:18,stuName:'zhangsan',stuAddress:'xinxiang',"stuSex":"M"},
  {stuNo:'stu006',stuAge:20,stuName:'zhangsan',stuAddress:'xinxiang',"stuSex":"F"},
  {stuNo:'stu007',stuAge:28,stuName:'zhangsan',stuAddress:'xinxiang',"stuSex":"M"},
  {stuNo:'stu008',stuAge:20,stuName:'zhangsan',stuAddress:'xinxiang',"stuSex":"F"},
  {stuNo:'stu009',stuAge:19,stuName:'zhangsan',stuAddress:'xinxiang',"stuSex":"M"},
  {stuNo:'stu010',stuAge:18,stuName:'zhangsan',stuAddress:'xinxiang',"stuSex":"F"},
]
const stusTemp = ref([])
const my_init=()=>{
  stusTemp.value=stus;
}
const fun01=()=>{
  alert("hello world")
}
const fun02=()=>{
  let sex = document.getElementById("txtSex").value
  stusTemp.value = stusTemp.value.filter((stu)=>{
    return stu.stuSex == sex 
  })

  console.log(stusTemp.value)
}
</script>
<style lang="less" scoped>
/* 样式表的地方 */
  .my-center{
    width: 400px;
    height:200px;
    align-self: center;
    border:1px solid red;
    /* border-radius:10px ; */
    border-top-right-radius: 10px;
    border-top-left-radius: 10px;
    margin: 0 auto;
  }
</style>

