<template>
    <div class="app-container">
        <!-- 查询表单 -->
        <el-form :inline="true" :model="formInline" class="demo-form-inline">
            <el-form-item label="name">
                <el-input v-model="formInline.name" placeholder="name"></el-input>
            </el-form-item>
            <el-form-item label="mobile">
                <el-input v-model="formInline.mobile" placeholder="mobile"></el-input>
            </el-form-item>
            <el-form-item>
                <el-button type="primary" icon="el-icon-search" @click="onSubmit">search</el-button>
            </el-form-item>
        </el-form>
        <!-- 按钮组 -->
        <div>
            <el-button type="primary" icon="el-icon-plus" @click="dialogVisible = true">add</el-button>
            <el-button type="primary" icon="el-icon-delete" @click="onDeleteSubmit">delete</el-button>
            <!-- add按钮对话框 -->
            <el-dialog
            title="add"
            :visible.sync="dialogVisible"
            width="30%"
            :before-close="handleClose">
                <el-form :rules="rules" :model="formElement" label-width="80px">
                    <el-form-item label="name">
                        <el-input v-model="formElement.name"></el-input>
                    </el-form-item>
                    <el-form-item label="ename">
                        <el-input v-model="formElement.ename"></el-input>
                    </el-form-item>
                    <el-form-item label="assistant_code">
                        <el-input v-model="formElement.assistant_code"></el-input>
                    </el-form-item>
                    <el-form-item label="type">
                        <el-input v-model="formElement.type"></el-input>
                    </el-form-item>
                    <el-form-item label="settle_id">
                        <el-input v-model="formElement.settle_id"></el-input>
                    </el-form-item>
                    <el-form-item label="contacts">
                        <el-input v-model="formElement.contacts"></el-input>
                    </el-form-item>
                    <el-form-item label="mobile" prop="mobile" :rules="rules.mobile">
                        <el-input v-model="formElement.mobile"></el-input>
                    </el-form-item>
                    <el-form-item label="tel" prop="tel" :rules="rules.tel">
                        <el-input v-model="formElement.tel"></el-input>
                    </el-form-item>
                    <el-form-item label="address">
                        <el-input v-model="formElement.address"></el-input>
                    </el-form-item>
                    <el-form-item label="fax">
                        <el-input v-model="formElement.fax"></el-input>
                    </el-form-item>
                    <el-form-item label="account">
                        <el-input v-model="formElement.account"></el-input>
                    </el-form-item>
                    <el-form-item label="pasword">
                        <el-input v-model="formElement.pasword"></el-input>
                    </el-form-item>
                    <el-form-item label="email" prop="email" :rules="rules.email">
                        <el-input v-model="formElement.email"></el-input>
                    </el-form-item>
                    <el-form-item label="create_by">
                        <el-input v-model="formElement.create_by"></el-input>
                    </el-form-item>
                    <el-form-item label="creator">
                        <el-input v-model="formElement.creator"></el-input>
                    </el-form-item>
                    <el-form-item label="created_time">
                        <el-input v-model="formElement.created_time"></el-input>
                    </el-form-item>
                    <el-form-item label="updated_by">
                        <el-input v-model="formElement.updated_by"></el-input>
                    </el-form-item>
                    <el-form-item label="modifier">
                        <el-input v-model="formElement.modifier"></el-input>
                    </el-form-item>
                    <el-form-item label="updated_time">
                        <el-input v-model="formElement.updated_time"></el-input>
                    </el-form-item>
                    <el-form-item label="status">
                        <el-input v-model="formElement.status"></el-input>
                    </el-form-item>
                    <el-form-item label="version">
                        <el-input v-model="formElement.version"></el-input>
                    </el-form-item>
                    
                    <el-form-item>
                        <el-button @click="onAddCancelSubmit">cancel</el-button>
                        <el-button type="primary" @click="onAddSubmit">add</el-button>
                    </el-form-item>
                    </el-form>
            </el-dialog>
        </div>
        <!-- 表格 -->
        <div style="margin-top: 20px">
            <el-table
                ref="multipleTable"
                stripe
                border
                height="350"
                max-height="350"
                :data="currentTableData"
                tooltip-effect="dark"
                style="width: 100%"
                @selection-change="handleSelectionChange">
                <el-table-column
                fixed="left"
                type="selection"
                width="55">
                </el-table-column>
                <el-table-column
                prop="id"
                label="id"
                width="120">
                </el-table-column>
                <el-table-column
                prop="name"
                label="name"
                width="120">
                </el-table-column>
                <el-table-column
                prop="ename"
                label="ename"
                width="120">
                </el-table-column>
                <el-table-column
                prop="assistant_code"
                label="assistant_code"
                width="120">
                </el-table-column>
                <el-table-column
                prop="type"
                label="type"
                width="120">
                </el-table-column>
                <el-table-column
                prop="settle_id"
                label="settle_id"
                width="120">
                </el-table-column>
                <el-table-column
                prop="contacts"
                label="contacts"
                width="120">
                </el-table-column>
                <el-table-column
                prop="mobile"
                label="mobile"
                width="120">
                </el-table-column>
                <el-table-column
                prop="tel"
                label="tel"
                width="120">
                </el-table-column>
                <el-table-column
                prop="address"
                label="address"
                width="120">
                </el-table-column>
                <el-table-column
                prop="fax"
                label="fax"
                width="120">
                </el-table-column>
                <el-table-column
                prop="account"
                label="account"
                width="120">
                </el-table-column>
                <el-table-column
                prop="pasword"
                label="pasword"
                width="120">
                </el-table-column>
                <el-table-column
                prop="email"
                label="email"
                width="120">
                </el-table-column>
                <el-table-column
                prop="create_by"
                label="create_by"
                width="120">
                </el-table-column>
                <el-table-column
                prop="creator"
                label="creator"
                width="120">
                </el-table-column>
                <el-table-column
                prop="created_time"
                label="created_time"
                width="120">
                </el-table-column>
                <el-table-column
                prop="updated_by"
                label="updated_by"
                width="120">
                </el-table-column>
                <el-table-column
                prop="modifier"
                label="modifier"
                width="120">
                </el-table-column>
                <el-table-column
                prop="updated_time"
                label="updated_time"
                width="120">
                </el-table-column>
                <el-table-column
                prop="status"
                label="status"
                width="120">
                </el-table-column>
                <el-table-column
                prop="version"
                label="version"
                width="120">
                </el-table-column>
                <el-table-column
                fixed="right"
                label="操作"
                width="100">
                <template slot-scope="scope">
                    <el-button @click="handleUpdateClick(scope.row)" type="primary" size="small">update</el-button>
                </template>
                </el-table-column>
            </el-table>
            <!-- update按钮对话框 -->
            <el-dialog
            title="update"
            :visible.sync="updateDialogVisible"
            width="30%"
            :before-close="handleClose">
                <el-form :model="formElement" label-width="80px">
                    <el-form-item label="name">
                        <el-input v-model="formElement.name"></el-input>
                    </el-form-item>
                    <el-form-item label="ename">
                        <el-input v-model="formElement.ename"></el-input>
                    </el-form-item>
                    <el-form-item label="assistant_code">
                        <el-input v-model="formElement.assistant_code"></el-input>
                    </el-form-item>
                    <el-form-item label="type">
                        <el-input v-model="formElement.type"></el-input>
                    </el-form-item>
                    <el-form-item label="settle_id">
                        <el-input v-model="formElement.settle_id"></el-input>
                    </el-form-item>
                    <el-form-item label="contacts">
                        <el-input v-model="formElement.contacts"></el-input>
                    </el-form-item>
                    <el-form-item label="mobile" prop="mobile" :rules="rules.mobile">
                        <el-input v-model="formElement.mobile"></el-input>
                    </el-form-item>
                    <el-form-item label="tel" prop="tel" :rules="rules.tel">
                        <el-input v-model="formElement.tel"></el-input>
                    </el-form-item>
                    <el-form-item label="address">
                        <el-input v-model="formElement.address"></el-input>
                    </el-form-item>
                    <el-form-item label="fax">
                        <el-input v-model="formElement.fax"></el-input>
                    </el-form-item>
                    <el-form-item label="account">
                        <el-input v-model="formElement.account"></el-input>
                    </el-form-item>
                    <el-form-item label="pasword">
                        <el-input v-model="formElement.pasword"></el-input>
                    </el-form-item>
                    <el-form-item label="email" prop="email" :rules="rules.email">
                        <el-input v-model="formElement.email"></el-input>
                    </el-form-item>
                    <el-form-item label="create_by">
                        <el-input v-model="formElement.create_by"></el-input>
                    </el-form-item>
                    <el-form-item label="creator">
                        <el-input v-model="formElement.creator"></el-input>
                    </el-form-item>
                    <el-form-item label="created_time">
                        <el-input v-model="formElement.created_time"></el-input>
                    </el-form-item>
                    <el-form-item label="updated_by">
                        <el-input v-model="formElement.updated_by"></el-input>
                    </el-form-item>
                    <el-form-item label="modifier">
                        <el-input v-model="formElement.modifier"></el-input>
                    </el-form-item>
                    <el-form-item label="updated_time">
                        <el-input v-model="formElement.updated_time"></el-input>
                    </el-form-item>
                    <el-form-item label="status">
                        <el-input v-model="formElement.status"></el-input>
                    </el-form-item>
                    <el-form-item label="version">
                        <el-input v-model="formElement.version"></el-input>
                    </el-form-item>
                    
                    <el-form-item>
                        <el-button @click="onUpdateCancelSubmit">cancel</el-button>
                        <el-button type="primary" @click="onUpdateSubmit">save</el-button>
                    </el-form-item>
                    </el-form>
            </el-dialog>
            <div style="margin-top: 20px">
                <el-button @click="toggleSelection()">cancel choose</el-button>
            </div>
        </div>
        <!-- 分页 -->
        <div class="block" style="margin-top: 20px">
            <el-pagination
            @size-change="handleSizeChange"
            @current-change="handleCurrentChange"
            :current-page="currentPage"
            :page-sizes="[10, 20, 30, 40]"
            :page-size="100"
            layout="total, sizes, prev, pager, next, jumper"
            :total="400">
            </el-pagination>
        </div>
    </div>
</template>
<script>
  export default {
    data() {
      return {
        formInline: {
          name: '',
          mobile: ''
        },
        dialogVisible: false,
        updateDialogVisible: false,
        // add 和 update 所使用的表格数据
        formElement: {
          id: '',
          name: '',
          ename: '',
          assistant_code: '',
          type: '',
          settle_id: '',
          contacts: '',
          mobile: '',
          tel: '',
          address: '',
          fax: '',
          account: '',
          pasword: '',
          email: '',
          create_by: '',
          creator: '',
          created_time: '',
          updated_by: '',
          modifier: '',
          updated_time: '',
          status: '',
          version: ''
        },
        row: '', //当前编辑行的数据
        tableData: [{
          id: '1349528394387292160',
          name: '上海佰诚医药供应链管理有限公司',
          ename: 'a',
          assistant_code: 'SHBC',
          type: '1349526039734386688',
          settle_id: '1328326480601677824',
          contacts: '甘磊',
          mobile: '13816677831',
          tel: '021-33282800',
          address: '上海市闵行区申滨南路1126号龙湖天街C栋306室',
          fax: '',
          account: '',
          pasword: '',
          email: '',
          create_by: '1',
          creator: '系统管理员',
          created_time: '20210121090705',
          updated_by: '',
          modifier: '系统管理员',
          updated_time: '2021-01-21 17:07:23',
          status: '',
          version: ''
        },{
          id: '1349528394387292161',
          name: '上海医药供应链管理有限公司',
          ename: 'a',
          assistant_code: 'SHBC',
          type: '1349526039734386688',
          settle_id: '1328326480601677824',
          contacts: '甘磊',
          mobile: '13816677831',
          tel: '021-33282800',
          address: '上海市闵行区申滨南路1126号龙湖天街C栋306室',
          fax: '',
          account: '',
          pasword: '',
          email: '',
          create_by: '1',
          creator: '系统管理员',
          created_time: '20210121090705',
          updated_by: '',
          modifier: '系统管理员',
          updated_time: '2021-01-21 17:07:23',
          status: '',
          version: ''
        },{
          id: '1349528394387292162',
          name: '上海佰诚医药有限公司',
          ename: 'a',
          assistant_code: 'SHBC',
          type: '1349526039734386688',
          settle_id: '1328326480601677824',
          contacts: '甘磊',
          mobile: '13816677831',
          tel: '021-33282800',
          address: '上海市闵行区申滨南路1126号龙湖天街C栋306室',
          fax: '',
          account: '',
          pasword: '',
          email: '',
          create_by: 1,
          creator: '系统管理员',
          created_time: '20210121090705',
          updated_by: '',
          modifier: '系统管理员',
          updated_time: '2021-01-21 17:07:23',
          status: '',
          version: ''
        },{
          id: '1349528394387292163',
          name: '北京佰诚医药供应链管理有限公司',
          ename: 'a',
          assistant_code: 'SHBC',
          type: '1349526039734386688',
          settle_id: '1328326480601677824',
          contacts: '甘磊',
          mobile: '13816677831',
          tel: '021-33282800',
          address: '上海市闵行区申滨南路1126号龙湖天街C栋306室',
          fax: '',
          account: '',
          pasword: '',
          email: '',
          create_by: '1',
          creator: '系统管理员',
          created_time: '20210121090705',
          updated_by: '',
          modifier: '系统管理员',
          updated_time: '2021-01-21 17:07:23',
          status: '',
          version: ''
        },{
          id: '1349528394387292164',
          name: '北京佰诚医药有限公司',
          ename: 'a',
          assistant_code: 'SHBC',
          type: '1349526039734386688',
          settle_id: '1328326480601677824',
          contacts: '甘磊',
          mobile: '13816677831',
          tel: '021-33282800',
          address: '上海市闵行区申滨南路1126号龙湖天街C栋306室',
          fax: '',
          account: '',
          pasword: '',
          email: '',
          create_by: '1',
          creator: '系统管理员',
          created_time: '20210121090705',
          updated_by: '',
          modifier: '系统管理员',
          updated_time: '2021-01-21 17:07:23',
          status: '',
          version: ''
        }],
        currentTableData: [],
        multipleSelection: [],
        currentPage: 1,
        // 校验规则
        rules: {
            mobile: [
                {
                    required: true,
                    pattern:  /^1[0-9]{10}$/,
                    message: "mobile error !",
                    trgger: "blur"
                }
            ],
            tel: [
                {
                    required: true,
                    pattern: /^([0-9]{3,4}-)?[0-9]{7,8}$/,
                    message: "tel error !",
                    trgger: "blur"
                }
            ],
            email: [
                {
                    required: true,
                    pattern: /[\w!#$%&'*+/=?^_`{|}~-]+(?:\.[\w!#$%&'*+/=?^_`{|}~-]+)*@(?:[\w](?:[\w-]*[\w])?\.)+[\w](?:[\w-]*[\w])?/,
                    message: "email error !",
                    trgger: "blur"
                }
            ]
        }
      }
    },
    created() {
        //将持久数据（存储在data中）赋给当前table
        this.currentTableData = this.tableData;
    },
    methods: {
        //搜索提交按钮
      onSubmit() {
          let that = this;
          let name = that.formInline.name;
          let mobile = that.formInline.mobile;
          let currentData = that.currentTableData;
          let resultData = [];
          if(name !== '' && mobile !== ''){
              for(let i = 0; i < currentData.length; i++){
                  if(currentData[i].mobile === mobile && currentData[i].name === name){
                      resultData.push(currentData[i])
                  }
              }
          }else if(name == '' && mobile !== ''){
              for(let i = 0; i < currentData.length; i++){
                  if(currentData[i].mobile === mobile){
                      resultData.push(currentData[i])
                  }
              }
          }else if(name !== '' && mobile == ''){
              for(let i = 0; i < currentData.length; i++){
                  if(currentData[i].name === name){
                      resultData.push(currentData[i])
                  }
              }
          }else {
              that.currentTableData = currentData;
              return;
          }
          that.currentTableData = resultData;
          this.$message('submit!');
      },
    //   按钮组
      handleClose(done) {
        let that = this;
        this.$confirm('确认关闭？')
          .then(_ => {
            that.formElement = {
            id: '',
            name: '',
            ename: '',
            assistant_code: '',
            type: '',
            settle_id: '',
            contacts: '',
            mobile: '',
            tel: '',
            address: '',
            fax: '',
            account: '',
            pasword: '',
            email: '',
            create_by: '',
            creator: '',
            created_time: '',
            updated_by: '',
            modifier: '',
            updated_time: '',
            status: '',
            version: ''
          };
            done();
          })
          .catch(_ => {});
      },
      //add按钮
      onAddSubmit() {
          let that = this;
          that.formElement.id = that.tableData[that.tableData.length-1].id + 1;
          that.currentTableData.push(that.formElement);
          that.formElement = {
            id: '',
            name: '',
            ename: '',
            assistant_code: '',
            type: '',
            settle_id: '',
            contacts: '',
            mobile: '',
            tel: '',
            address: '',
            fax: '',
            account: '',
            pasword: '',
            email: '',
            create_by: '',
            creator: '',
            created_time: '',
            updated_by: '',
            modifier: '',
            updated_time: '',
            status: '',
            version: ''
          };
          that.tableData = that.currentTableData;      
          that.dialogVisible = false;
      },
      //add的取消按钮
      onAddCancelSubmit(){
          let that = this;
          that.formElement = {
            id: '',
            name: '',
            ename: '',
            assistant_code: '',
            type: '',
            settle_id: '',
            contacts: '',
            mobile: '',
            tel: '',
            address: '',
            fax: '',
            account: '',
            pasword: '',
            email: '',
            create_by: '',
            creator: '',
            created_time: '',
            updated_by: '',
            modifier: '',
            updated_time: '',
            status: '',
            version: ''
          };
          that.dialogVisible = false;
      },
      onDeleteSubmit() {
          let that = this;
          if(that.multipleSelection.length == 0){
            this.$message('no item has been choosed!');
            return;
          }
          for(let i = 0; i < that.multipleSelection.length; i++){
            let index = that.currentTableData.indexOf(this.multipleSelection[i])
            that.currentTableData.splice(index, 1);
          }
          that.tableData = that.currentTableData;       
      },
    //   表格
      handleUpdateClick(row) {
          let that = this;
          that.updateDialogVisible = true;
          // 拿到当前行的数据
          that.row = row;
          that.formElement = Object.assign({}, row);
      },
      //更新按钮
      onUpdateSubmit(){
        let that = this;
        let index = that.currentTableData.indexOf(that.row);
        that.currentTableData.splice(index, 1, that.formElement); 
        that.formElement = {
            id: '',
            name: '',
            ename: '',
            assistant_code: '',
            type: '',
            settle_id: '',
            contacts: '',
            mobile: '',
            tel: '',
            address: '',
            fax: '',
            account: '',
            pasword: '',
            email: '',
            create_by: '',
            creator: '',
            created_time: '',
            updated_by: '',
            modifier: '',
            updated_time: '',
            status: '',
            version: ''
        };
        that.tableData = that.currentTableData;      
        that.updateDialogVisible = false;
      },
      //更新取消按钮
      onUpdateCancelSubmit(){
          let that = this;
          console.log(that.row);
          let index = that.currentTableData.indexOf(that.row);
          that.currentTableData.splice(index, 1, that.row); 
          that.formElement = {
            id: '',
            name: '',
            ename: '',
            assistant_code: '',
            type: '',
            settle_id: '',
            contacts: '',
            mobile: '',
            tel: '',
            address: '',
            fax: '',
            account: '',
            pasword: '',
            email: '',
            create_by: '',
            creator: '',
            created_time: '',
            updated_by: '',
            modifier: '',
            updated_time: '',
            status: '',
            version: ''
          };
          that.tableData = that.currentTableData;      
          that.updateDialogVisible = false;
      },
      //取消选择
      toggleSelection(rows) {
        if (rows) {
          rows.forEach(row => {
            this.$refs.multipleTable.toggleRowSelection(row);
          });
        } else {
          this.$refs.multipleTable.clearSelection();
        }
      },
      handleSelectionChange(val) {
        this.multipleSelection = val;
      },
    //   分页
      handleSizeChange(val) {
        console.log(`每页 ${val} 条`);
      },
      handleCurrentChange(val) {
        console.log(`当前页: ${val}`);
      }
    }
  }
</script>

<style scoped>
.app-container {
    margin-left: 60px;
}
</style>