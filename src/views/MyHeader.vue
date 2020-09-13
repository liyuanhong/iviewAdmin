<style scoped>

</style>

<template>
    <Header :style='{"padding":"0px"}'>
        <Icon @click.native="collapsedSider" :style="{float: 'left',width:'64px',height:'64px','line-height':'64px'}" type="md-menu" size="24"></Icon>
    </Header>
</template>

<script>
export default {
    name: "my-header",
    data(){
        return {

        }
    },
    methods: {
        collapsedSider () {
            this.$emit('aaa');
        }
    }
}
</script>