<template>

    <!-- <div>
        <el-row :gutter="0">
            <el-col> 是 Element UI 组件库中的一个组件，用于创建列布局。
            :span="12" 表示该列跨越了网格系统中的 12 个栅格单位，即占据了整个行的宽度。
            这意味着这个列会占据布局的一半，因为 Element UI 默认的栅格系统是 24 格。 
            <el-col :span="6">
                <div style="width: 100%; height: 300px; background-color: aquamarine;"></div>
            </el-col>
            <el-col :span="18">
                <div style="width: 100%; height: 300px; background-color: red;"></div>
            </el-col>
        </el-row>
    </div> -->


    <div>
        <el-row gutter="10">

            <el-col :span="6">
                <div style="padding: 10px; border: 1px solid #ccc; 
                    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);border-radius: 10px;text-align: center;">
                    <img style="width: 80%;" src="@/assets/logo.png" alt="">
                    <div style="text-align: center;">这是一段很牛b的描述</div>
                    <div style="text-align: center;color: red;">价格 ￥99.00</div>
                </div>
            </el-col>
            <el-col :span="6">
                <div style="padding: 10px; border: 1px solid #ccc; 
                    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);border-radius: 10px;text-align: center;">
                    <img style="width: 80%;" src="@/assets/logo.png" alt="">
                    <div style="text-align: center;">这是一段很牛b的描述</div>
                    <div style="text-align: center;color: red;">价格 ￥99.00</div>
                </div>
            </el-col>
            <el-col :span="6">
                <div style="padding: 10px; border: 1px solid #ccc; 
                    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);border-radius: 10px;text-align: center;">
                    <img style="width: 80%;" src="@/assets/logo.png" alt="">
                    <div style="text-align: center;">这是一段很牛b的描述</div>
                    <div style="text-align: center;color: red;">价格 ￥99.00</div>
                </div>
            </el-col>
            <el-col :span="6">
                <div style="padding: 10px; border: 1px solid #ccc; 
                    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);border-radius: 10px;text-align: center;">
                    <img style="width: 80%;" src="@/assets/logo.png" alt="">
                    <div style="text-align: center;">这是一段很牛b的描述</div>
                    <div style="text-align: center;color: red;">价格 ￥99.00</div>
                </div>
            </el-col>

        </el-row>

        <el-row>
            <el-col :span="24">
                <el-button type="info" plain>Element独特的按钮</el-button>
                <el-button type="primary">主要按钮</el-button>
                <el-button type="success">成功按钮</el-button>
                <el-button type="info">信息按钮</el-button>
                <el-button type="warning">警告按钮</el-button>
                <el-button type="danger">危险按钮</el-button>

                <el-button type="primary" round>主要按钮</el-button>
                <el-button type="success" round>成功按钮</el-button>
                <el-button type="info" round>信息按钮</el-button>

                <el-button icon="el-icon-search" circle></el-button>
                <el-button type="primary" icon="el-icon-edit" circle></el-button>
                <el-button type="success" icon="el-icon-check" circle></el-button>
                <el-button type="info" icon="el-icon-message" circle></el-button>
                <el-button type="warning" icon="el-icon-star-off" circle></el-button>
                <el-button type="danger" icon="el-icon-delete" circle></el-button>
            </el-col>
        </el-row>

        <el-row style="margin-top: 20px;">
            <el-col>

                <el-input style="width: 200px;" v-model="value" placeholder="请输入内容"></el-input>
                <el-input type="textarea" style="width: 200px;" v-model="value1" placeholder="找工作好难"></el-input>

                <el-input show-password style="width: 200px;" v-model="password" placeholder="请输入密码"></el-input>

                <el-input style="width: 200px;" v-model="value2" placeholder="请输入内容"
                    prefix-icon="el-icon-search"></el-input>
                <el-input clearable style="width: 200px;" v-model="value2" placeholder="请输入内容"
                    suffix-icon="el-icon-search"></el-input>

                <el-button>搜索</el-button>

            </el-col>

        </el-row>

    </div>
</template>

<script>
export default {
    name: 'Element',
    data() {
        return {
            value: '',
            value1:'',
            value2: '',
            password:'',
        }
    }
}
</script>

<style></style>