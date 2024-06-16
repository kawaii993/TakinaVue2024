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
        <el-row :gutter="10">

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


        <el-row style="margin: 20px 0;">
            <el-autocomplete style="width:300px;" placeholder="请输入内容，我来帮你猜一猜" :fetch-suggestions="querySearch"
                :trigger-on-focus="false" v-model="value3">

            </el-autocomplete>
        </el-row>

        <el-select v-model="select" @change="changeSelect">
            <el-option value="香蕉"></el-option>
            <el-option value="橘子"></el-option>
            <el-option value="菠萝"></el-option>
        </el-select>

        <el-select v-model="select1" @change1="changeSelect">
            <el-option v-for="item in fruits" :key="item.id" :label="item.name" :value="item.name"></el-option>
        </el-select>

        <el-select v-model="select2" @change="changeSelectUser">
            <el-option v-for="item in users" :key="item.card" :label="item.name" :value="item.card"></el-option>
        </el-select>
        <el-select v-model="select2" @change="changeSelectUser" multiple>
            <el-option v-for="item in users" :key="item.card" :label="item.name" :value="item.card"></el-option>
        </el-select>

        <el-select v-model="select2" @change="changeSelectUser" filterable>
            <el-option v-for="item in users1" :key="item.card" :label="item.label" :value="item.card"></el-option>
        </el-select>


        <el-row>
            <el-radio-group v-model="radio" @change="selectRadio">
                <el-radio label="男"></el-radio>
                <el-radio label="女"></el-radio>
            </el-radio-group>

            <el-checkbox-group v-model="checkList">
                <el-checkbox label="男"></el-checkbox>
                <el-checkbox label="女"></el-checkbox>
            </el-checkbox-group>

            <el-date-picker v-model="date" type="date" placeholder="选择日期" value-format="yyyy-MM-dd"
                @change="changeDate"></el-date-picker>
            <el-date-picker v-model="datetime" type="datetime" placeholder="选择日期时间" value-format="yyyy-MM-dd HH:mm:ss"
                @change="changeDateTime"></el-date-picker>

            <el-date-picker v-model="daterange" type="daterange" start-placeholder="开始日期" end-placeholder="结束日期"
                value-format="yyyy-MM-dd">

            </el-date-picker>


        </el-row>

        <el-row style="margin: 80px 0;">
            <el-table :data="tableData" border :header-cell-style="{ background: 'aliceblue',fontSize:'16px'}">
                <el-table-column label="序号" prop="id" align="center"></el-table-column>
                <el-table-column label="名称" prop="name" align="center"></el-table-column>
                <el-table-column label="年龄" prop="age" align="center"></el-table-column>
                <el-table-column label="地址" prop="address" align="center"></el-table-column>
                <el-table-column label="操作" align="center">
                    <template v-slot="scope">
                        <el-button type="primary" @click="edit(scope.row)">编辑</el-button>
                    </template>
                </el-table-column>
            </el-table>
        </el-row>


    </div>
</template>

<script>
import { Result } from 'element-ui';

export default {
    name: 'Element',
    data() {
        return {
            tableData: [
                { name: '眠羊', address: '湖北省武汉市', id: 1, age: '10' },
                { name: '眠羊', address: '湖北省武汉市', id: 1, age: '10' },
                { name: '眠羊', address: '湖北省武汉市', id: 1, age: '10' },
            ],
            value: '',
            value1: '',
            value2: '',
            value3: '',
            password: '',
            select: '',
            select1: '',
            select2: '',
            fruits: [
                { name: '苹果', id: 1 },
                { name: '橘子', id: 2 },
                { name: '香橙', id: 3 },
            ],
            coffees: [{ value: '1星巴克咖啡' }, { value: '1栖巢咖啡' }, { value: '2瑞幸咖啡' }, { value: '3库迪咖啡' }],
            users: [
                { name: '你怎么好笨', card: '12311212123' },
                { name: '又被小乔了', card: '12311212124' },
                { name: 'Cutey', card: '12311212125' },
            ],
            users1: [
                { label: '你怎么好笨', card: '12311212123' },
                { label: '又被小乔了', card: '12311212124' },
                { label: 'Cutey', card: '12311212125' },
            ],
            radio: '',
            checkList: [],
            date: '',
            datetime: '',
            daterange: '',
        }
    },
    methods: {
        querySearch(query, cb) {  // callback 回调
            let result = query ? this.coffees.filter(v => v.value.includes(query)) : this.coffees
            cb(result);
        },
        changeSelect() {
            console.log(this.select);
        },
        changeSelectUser() {
            console.log(this.select2);
        },
        selectRadio() {
            alert(this.radio);
        },
        changeDate() {
            console.log(this.date);
        },
        changeDateTime() {
            console.log(this.datetime);
        },
        edit(row){
            // alert(row.name)
            // this.$message.success(row.name)
            // this.$notify.success(row.name)
            this.$confirm( '这是什么个玩意儿' , '提示',{
                type:'warning'
            }).then(res => {
                this.$message.success('oi 点击了确认')
            }).catch(()=>{
                this.$message.warning('oi 点击了取消')
            })
        },
    }
}
</script>

<style></style>