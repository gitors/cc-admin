<!--头部组件-->
<style scoped>
.preview-header {
    padding-right: 10%;
    height: 60px;
    background: #4a5161;
    text-align: right;
}
ul {
    display: inline-block !important;
}
</style>
<template>
    <div class="preview-header">
        <Menu mode="horizontal" theme="dark" active-name="1" @on-select="menuSelected">
            <div class="preview-header-nav">
                <MenuItem name="index">
                    <Icon type="ios-home-outline"></Icon>
                    首页
                </MenuItem>
                <MenuItem name="index">
                    <Icon type="ios-keypad"></Icon>
                    前端
                </MenuItem>
                <MenuItem name="index">
                    <Icon type="ios-analytics"></Icon>
                    后端
                </MenuItem>
                <MenuItem name="index">
                    <Icon type="ios-paper"></Icon>
                    中间件
                </MenuItem>
                <MenuItem name = "6">
                    <Tooltip content="回车搜索……" placement="bottom">
                        <i-input v-model="value" placeholder="Search something..." style="width: 200px;" @on-enter="search"></i-input>
                    </Tooltip>
                </MenuItem>
                <MenuItem name="5">
                    <div v-if="!logined"> 登陆 - 注册</div>
                    <div class="user-dropdown-menu-con" v-if="logined">
                        <Row type="flex" justify="end" align="middle" class="user-dropdown-innercon">
                            <Dropdown transfer trigger="click" @on-click="handleClickUserDropdown" style="margin-right: 10px">
                                <DropdownMenu slot="list">
                                    <DropdownItem name="userHome" divided>发帖</DropdownItem>
                                    <DropdownItem name="loginout" divided>发教程</DropdownItem>
                                    <DropdownItem name="setting" divided>设置</DropdownItem>
                                </DropdownMenu>
                                <Icon type="plus-round" size="20"></Icon>
                                <Icon type="arrow-down-b"></Icon>
                            </Dropdown>
                            <Dropdown transfer trigger="click" @on-click="handleClickUserDropdown">
                                <DropdownMenu slot="list">
                                    <DropdownItem name="msgCenter">
                                        消息中心<Badge count="10"></Badge>
                                    </DropdownItem>
                                    <DropdownItem name="userHome" >个人中心</DropdownItem>
                                    <DropdownItem name="setting" divided>设置</DropdownItem>
                                    <DropdownItem name="loginout" >退出登录</DropdownItem>
                                </DropdownMenu>
                                <Tooltip content="有100条未读消息" placement="bottom">
                                    <Badge dot>
                                        <Avatar icon="person" style="background: #619fe7;margin-left:10px;" src="https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=3448484253,3685836170&amp;fm=27&amp;gp=0.jpg"></Avatar>
                                    </Badge>
                                </Tooltip>
                                <Icon type="arrow-down-b"></Icon>
                            </Dropdown>
                        </Row>
                    </div>
                </MenuItem>
            </div>
        </Menu>
    </div>
</template>

<script>
export default {
    data () {
        return {
            logined: true,
            navList: [],
            vslue13: '',
            select13: '',
            value: ''
        };
    },
    methods: {
        handleClickUserDropdown: function (s) {
            switch (s) {
                case 'userHome': {
                    let params = {
                        userId: 1
                    };
                    this.$router.push({
                        name: 'userHome',
                        params: params
                    });
                }
            }
        },
        search() {
            alert('搜索关键词：' + this.value);
        },
        menuSelected (name) {
            if (name !== '5' && name !== '6'){
                this.$router.push({
                    name: name
                });
            }
        }
    }
};
</script>