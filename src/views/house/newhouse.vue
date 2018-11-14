<template>
  <div class="app-container newhouse" id="newhouse">

    <div class="filter-container">
        <el-input placeholder="地址/标题" v-model="listQuery.title" style="width: 200px;" class="filter-item" />
        <el-input placeholder="ID" v-model="listQuery.id" style="width: 200px;" class="filter-item" />
        <el-button class="filter-item" type="primary" icon="el-icon-search" @click="handleFilter">搜索</el-button>
        <el-button class="filter-item" type="danger" icon="el-icon-delete" @click="handleDelete">删除</el-button>
        <el-button class="filter-item" style="margin-left: 10px;" type="primary" icon="el-icon-edit" @click="handleCreate">编辑</el-button>
        <el-button class="filter-item" style="margin-left: 10px;" type="primary" icon="el-icon-edit" @click="handleCreate">添加</el-button>
    </div>

    <el-table border :data="tableData" style="width: 100%" class="tablelist" @selection-change="handleSelectionChange">
        <el-table-column label="序号" prop="id" align="center" width="65">
            <template slot-scope="scope">
                <span>{{ scope.$index+1}}</span>
            </template>
        </el-table-column>
        <el-table-column type="selection" align="center"></el-table-column>
        <el-table-column label="id" prop="id" width="50"></el-table-column>
        <el-table-column label="标题" prop="title" width="300"></el-table-column>
        <el-table-column label="显示方式" prop="showtype" width="80"></el-table-column>
        <el-table-column label="区域" prop="zone" width="100"></el-table-column>
        <el-table-column label="地址" prop="address" width="150"></el-table-column>
        <el-table-column label="建造年份" prop="buildyear" width="100"></el-table-column>
        <el-table-column label="挂牌价格" prop="price" width="100"></el-table-column>
        <el-table-column label="挂牌时间" prop="showtime" width="80"></el-table-column>
        <el-table-column label="交付时间" prop="totime" width="80"></el-table-column>
        <el-table-column label="房源状态" prop="status" width="60"></el-table-column>
        <el-table-column label="开发商" prop="dev"></el-table-column>
        <el-table-column label="推荐度" prop="recommend" width="80"></el-table-column>
        <el-table-column label="Code" prop="code"></el-table-column>
        <el-table-column align="center" label="操作" width="160">
            <template slot-scope="scope">
                <el-button size="mini" type="primary" @click="handleEdit(scope.$index, scope.row)">管理</el-button>
                <el-button size="mini" type="primary" @click="handleDelete(scope.$index, scope.row)">预览</el-button>
            </template>
        </el-table-column>
    </el-table>

    <el-pagination class="pagebox" :current-page="currentPage" background layout="prev, pager, next, jumper" :total="100"></el-pagination>

    

  </div>
</template>

<script>

export default {
  name: 'ComplexTable',
  data() {
    return {
        tableData: [{
            id:'123',
            title: '标题内容',
            showtype: '默认',
            zone:'中国',
            address: '上海市普陀区金沙江路 1518 弄',
            buildyear:2000,
            price:199999,
            showtime:'2014-05-19',
            totime:'2018年',
            status:'A',
            dev:'Westbank',
            recommend:'155',
            code:'20140519093425869000000'
        }, {
            id:'123',
            title: '标题内容',
            showtype: '默认',
            zone:'中国',
            address: '上海市普陀区金沙江路 1518 弄',
            buildyear:2000,
            price:199999,
            showtime:'2014-05-19',
            totime:'2018年',
            status:'A',
            dev:'Westbank',
            recommend:'155',
            code:'20140519093425869000000'
        }, {
            id:'123',
            title: '标题内容',
            showtype: '默认',
            zone:'中国',
            address: '上海市普陀区金沙江路 1518 弄',
            buildyear:2000,
            price:199999,
            showtime:'2014-05-19',
            totime:'2018年',
            status:'A',
            dev:'Westbank',
            recommend:'155',
            code:'20140519093425869000000'
        }, {
            id:'123',
            title: '标题内容',
            showtype: '默认',
            zone:'中国',
            address: '上海市普陀区金沙江路 1518 弄',
            buildyear:2000,
            price:199999,
            showtime:'2014-05-19',
            totime:'2018年',
            status:'A',
            dev:'Westbank',
            recommend:'155',
            code:'20140519093425869000000'
        }],
        importanceOptions: [1, 2, 3],
        typeOptions:[1,2,3,4,5],
        listQuery: {
            id:'',
            importance: undefined,
            title: undefined,
            type: undefined,
        },
        currentPage:1,
        multipleSelection:[]
    }
  },
  created() {
        
        // this.$axios.get(`https://192.168.0.158:9090/api/values/add`, {
        //     params:{

        //     }
        // }).then((res)=> {
        //     console.log(res.data)
        // })
  },
  components:{
      
  },
  methods: {
    handleSizeChange(val) {
        console.log(`每页 ${val} 条`);
    },
    handleCurrentChange(val) {
        console.log(`当前页: ${val}`);
    },
    handleFilter(){
        //搜索
    },
    handleCreate() {
        // 添加
        this.$router.push('article');
    },
    handleEdit(){
        //编辑
        this.$router.push('article');
    },
    handleDelete(index,row) {
        // 删除
        //需要后台交互，删除的同时后台接口返回相应的数据
        this.$notify({
            title: '成功',
            message: '删除成功',
            type: 'success',
            duration: 2000
        })
        this.tableData.splice(index, 1)
    },
    handleSelectionChange(val){
        //勾选复选框
        this.multipleSelection = val;
        console.log(this.multipleSelection)
    }
  }
}
</script>

<style scoped>
    .tablelist {margin-top: 30px;}
    .pagebox {margin-top: 50px;}
    .dialog {margin:auto;height: 80vh;width: 80%;}
</style>

