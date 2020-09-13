<style scoped>
div ::-webkit-scrollbar {
  display: none;
}

</style>

<template>
<div class="layout" :style='{"position":"fixed","height":"100%","width":"100%"}'>
  <Layout :style='{"position":"fixed","height":"100%","width":"100%"}'>
    <Sider hide-trigger collapsible :collapsed-width="78" v-model="isCollapsed" :style='{"height":"100%","overflow-y":"auto","overflow":"visible"}'>
      <MySider ref="mySider"></MySider>
    </Sider>
    <Layout :style='{"height":"100%","z-index":"500"}'>
        <Header :style='{"position":"fixed","width":"100%","padding":"0px"}'>
          <MyHeader @aaa="collapsedSider"></MyHeader>
        </Header>
        <Layout>
          <Breadcrumb :style='{"text-align":"left","padding-left":"10px","height":"32px","margin-top":"64px","padding-top":"5px"}'>
            <BreadcrumbItem to="/">Home</BreadcrumbItem>
            <BreadcrumbItem to="/components/breadcrumb">Components</BreadcrumbItem>
            <BreadcrumbItem>Breadcrumb</BreadcrumbItem>
          </Breadcrumb>
        </Layout>
        <Content :style='{"_margin-top":"64px","margin":"0px 10px","background":"#d4d4d4","margin-bottom":"10px"}'>
          <MyContent></MyContent>
        </Content>
        <Footer :style='{"background":"gray"}'>Footer</Footer>
    </Layout>
  </Layout>
</div>
</template>

<script>
import MySider from "./MySider"
import MyHeader from "./MyHeader"
import MyContent from "./MyContent"
export default {
    name: "home",
    data(){
        return {
          isCollapsed: false
        }
    },
    components: {
      MySider,
      MyHeader,
      MyContent
    },
    methods: {
      collapsedSider () {
        this.isCollapsed = !this.isCollapsed;
        this.$refs.mySider.isSpand = !this.isCollapsed;
      }
    }
}

</script>
