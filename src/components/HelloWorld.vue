<template>
  <yd-layout>
    <yd-navbar slot="navbar" title="NavBar">
        <router-link to="#" slot="left">
            <yd-navbar-back-icon></yd-navbar-back-icon>
        </router-link>
    </yd-navbar>
    <yd-cell-group>
        <yd-button @click.native="show1 = true" size="large">{{ping ? ping.value : '选择平台号'}}</yd-button>
        <yd-actionsheet :items="myItems1" v-model="show1" cancel="取消"></yd-actionsheet>

        <yd-cell-item >
          <span slot="left">这里是一个A链接</span>
          <span slot="right" @click="show1 = true">{{ping ? ping.label : '选择平台号'}}</span>
            <!-- <input slot="right" v-model="ping" @click="show1 = true" type="number" placeholder="请输入手机号"> -->
        </yd-cell-item>
        <yd-cell-item>
            <span slot="left">用户名：</span>
            <yd-input slot="right" required v-model="input1" max="20" placeholder="请输入用户名"></yd-input>
        </yd-cell-item>
        <yd-cell-item>
            <span slot="left">手机号：</span>
            <input slot="right" type="number" placeholder="请输入手机号">
        </yd-cell-item>
        <yd-cell-item arrow>
            <span slot="left">Time：</span>
            <yd-datetime type="time" v-model="datetime1" slot="right"></yd-datetime>
        </yd-cell-item>
        <yd-cell-item arrow>
            <span slot="left">Day：</span>
            <yd-datetime type="day" v-model="datetime2" slot="right"></yd-datetime>
        </yd-cell-item>
        <yd-cell-item arrow>
            <span slot="left">Month：</span>
            <yd-datetime type="month" v-model="datetime3" slot="right"></yd-datetime>
        </yd-cell-item>
        <yd-cell-item arrow>
            <span slot="left">Date：</span>
            <yd-datetime type="date" v-model="datetime4" slot="right"></yd-datetime>
        </yd-cell-item>
        <yd-cell-item arrow>
            <span slot="left">DateTime：</span>
            <yd-datetime type="datetime" v-model="datetime5" slot="right"></yd-datetime>
        </yd-cell-item>
        <yd-cell-item arrow type="label">
            <span slot="left">性别：</span>
            <select slot="right">
                <option value="">请选择性别</option>
                <option value="1">男</option>
                <option value="2">女</option>
                <option value="3">未知</option>
            </select>
        </yd-cell-item>
        <yd-cell-item arrow>
            <span slot="left">自定义模板：</span>
            <yd-datetime v-model="datetime6" :hourFormat="hourFormat" start-hour="1" end-hour="2" :minute-format="monthFormat" :month-format="monthFormat" :day-format="dayFormat" type="time" slot="right"></yd-datetime>
        </yd-cell-item>
    </yd-cell-group>
  <yd-layout>
</template>

<script type="text/babel">
    export default {
        data() {
            return {
                ping: '',
                input1: '',
                datetime1: '05:21',
                datetime2: '03-29',
                datetime3: '2016-06',
                datetime4: '2017-05-11',
                datetime5: '2017-05-11 06:06',
                datetime6: '2017-05-11',
                // hourFormat: '<span style="color:#F00;">{value}{{datetime1}}<i style="font-size: 12px;margin-left: 1px;">年</i></span>',
                hourFormat: 22+'年',
                monthFormat: '',
                dayFormat: '',
                yearFormat: {
                  'aa': 'aa',
                  'bb': 'bb',
                  'cc': 'cc',
                  'dd': 'dd'
                },
                show1: false,
                myItems1: [
                    {
                        label: '拍照',
                        value: "001",
                        callback: (label) => {
                            this.ping = label
                            /* 注意： callback: function() {} 和 callback() {}  这样是无法正常使用当前this的 */
                        }
                    },
                    {
                        label: '从相册中偷取',
                        value: "002",
                        callback: (label) => {
                            this.ping = label
                        }
                    }
                ]
            }
        },
        methods: {
          // callback: (label) => {
          //     this.ping = label
          // }
        }
    }
</script>

<style >
  .yd-datetime{
    bottom: -350px;
  }
  .yd-datetime-active{
    bottom: 0;
  }
  .yd-datetime-item:nth-child(2){
    display: none;
  }
</style>
