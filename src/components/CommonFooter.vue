<template>
        <ul :style="'background:' + bgColor" class="footer">
            <li class="footer-menu" v-for="(menu,index) in menuList" :key="index">
                <router-link @click.native="selectMenu(menu)" :to="menu.path">{{menu.title}}</router-link>
            </li>
        </ul>
</template>

<script>
export default {
    //父组件接收menuList值
    props : ['menuList'],
    data () {
        return {
            bgColor : ''
        }
    },
    methods:{
        selectMenu(menu){
            this.bgColor = menu.bgColor
            //子组件传值给父组件
            this.$emit('changeTitle',menu)
        }
    }
}
</script>

<style lang="scss" scoped>
.footer {
    display: flex;
    position: fixed;
    bottom: 0;
    width: 100%;
    height: 1rem;
    line-height: 1rem;
    background-color: #e54847;
    &-menu {
        flex-grow: 1;
        text-align: center;
        a{
            color: #fff;
            outline: none;
            &.router-link-exact-active{
                color: #000;
                font-size: 0.35rem;
            }
        }
    }
}
</style>