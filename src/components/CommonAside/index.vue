<template>
 <div class="aside">
        <el-menu default-active="1-4-1" class="el-menu-vertical-demo" @open="handleOpen" @close="handleClose" :collapse="isCollapse" 
        background-color="#525252"
        text-color="#fff"
        active-text-color="#060608"
        >
        <el-submenu v-for="item in hasChildren" :key="item.path" :index="item.name">
            <template slot="title">
            <i :class="`el-icon-${item.icon}`"></i>
            <span slot="title">{{item.label}}</span>
            </template>
            <el-submenu v-for="child in item.children" :key="child.path" :index="child.name">
              <span slot="title">{{child.label}}</span>
            </el-submenu>
        </el-submenu>
        <el-menu-item v-for="(item) in noChildren" :key="item.path" :index="item.name">
            <i :class="`el-icon-${item.icon}`"></i>
            <span slot="title">{{item.label}}</span>
        </el-menu-item>
        </el-menu>
        <el-button type="primary">大苏打撒是多少</el-button>
 </div>
</template>

<script>
import { Submenu } from 'element-ui';
 export default {
    name:'CommonAside',
    data() {
      return {
        isCollapse: false,
        menus:[
           {
            path:'/',
            name:'home',
            label:"首页",
            icon: 's-home',
          },
          {
            path:'/page1',
            name:'page1',
            label:"页面1",
            icon: 'setting',
          },
          {
            path:'/page2',
            name:'page2',
            label:"页面2",
            icon: 'setting',
          },
          {
            path:'/other',
            name:'other',
            label:"学生管理",
            icon: 'setting',
            children:[
              {
              path:'/page4',
              name:'page4',
              label:"页面4",
              icon: 'setting',
            },
             {
              path:'/page5',
              name:'page5',
              label:"页面5",
              icon: 'setting',
             },
             {
              path:'/page6',
              name:'page6',
              label:"页面6",
              icon: 'setting',
             },
            ]
          },

        ]
            
        
      };
    },
    computed:{
       noChildren(){
         return this.menus.filter(item=>!item.children)
       },
       hasChildren(){
         return this.menus.filter(item=>item.children)
       }
    },
    methods: {
      handleOpen(key, keyPath) {
        console.log(key, keyPath);
      },
      handleClose(key, keyPath) {
        console.log(key, keyPath);
      }
    }
  }
</script>

<style scoped>
.aside{
  height: 100%;
}

  .el-menu-vertical-demo:not(.el-menu--collapse) {
    width: 200px;
    min-height: 400px;
    height: 100%;
  }
  /* .el-menu-vertical-demo{
    height: 100%;
  } */
</style>