<style scoped>
.dropdown:hover {
    background:#68BBF3;
}

.ivu-select-dropdown {
    width: 150px;
    margin-left: 80px;
}
.sider_shrink {
    margin: 0px -10px;
}
.log_shrink {
    height:15px !important;
    margin-top:25px !important;
}
</style>

<template>
    <div>
        <div :style='{"height":"64px","border-bottom": "0.5px","border-color":"gray","border-bottom-style":"solid"}' width="auto">
            <img :src="logo" :style='{"height":"44px","border-radius":"10px","margin-top":"7px"}' :class='{log_shrink:!isSpand}'>
        </div>
        <div :class='{sider_shrink:!isSpand}'>
            <!-- 展开有子菜单 -->
            <Menu active-name="1-2" theme="dark" width="auto" :open-names="['1']" v-for="(item,index) in menus" :key="index" v-show="isSpand">
                <Submenu :name="item.menu">
                    <template slot="title">
                        <Icon type="ios-navigate"></Icon>
                        <span v-show="isSpand">{{ item.menu }}</span>
                    </template>
                    <MenuItem  v-show="isSpand" :name="item1" v-for="(item1,index1) in item.menuItem" :key="index1">{{ item1 }}</MenuItem>
                </Submenu>
            </Menu>
            <!-- 不展开有子菜单 -->
            <Dropdown :name="item.menu" class="dropdown" v-for="(item) in menus" :key="item.menu + 'a'" v-show="!isSpand" :style='{"width":"100%","padding":"20px 0"}' placement="right-start" :transfer="true">
                <span>
                    <Icon type="ios-navigate" style="font-size:22px;color:#eeeeee"></Icon>
                </span>
              <DropdownMenu slot="list" :style='{}'>
                  <DropdownItem :name="item1" v-for="(item1,index1) in item.menuItem" :key="index1 + 'b'" :style='{"width":"150px"}'>{{ item1 }}</DropdownItem>
              </DropdownMenu>
            </Dropdown>
            <!-- <Poptip trigger="hover" title="Title" content="content" v-show="!isSpand" placement="right-start" transfer="true">
                <span>
                    <Icon type="ios-navigate" :style='{"width":"78px","height":"78px"}'></Icon>
                </span>
            </Poptip> -->
        </div>
    </div>
</template>

<script>
export default {
    name: "my-sider",
    data(){
        return {
            "logo":"logo/logo.png",
            "isSpand": true,                //菜单栏是否展开
            "menus": [
                {"menu":"Item 1","menuItem":["Option 1","Option 2","Option 3"]},
                {"menu":"Item 2","menuItem":["Option 1","Option 2","Option 3"]},
                {"menu":"Item 3","menuItem":["Option 1","Option 2","Option 3"]},
                {"menu":"Item 4","menuItem":["Option 1","Option 2","Option 3"]}
            ]
        }
    }
}
</script>