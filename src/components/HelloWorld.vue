<template>
  <el-container style="height: 500px; border: 1px solid #eee">
    <el-container>
      <el-header style="text-align: right; font-size: 12px">
        <template>
          <!--<el-avatar shape="square" :size="60" :fit="fit" :src="url" style="float: left"></el-avatar>-->
          <el-button type="text" @click="open" style="color: aliceblue" icon="el-icon-info">helpを見る</el-button>
        </template>
      </el-header>

      <el-main>
        <el-main>
          <el-row :gutter="24" style="margin-top: 10px">
            <el-col :span="6" :offset="6">
              <el-input v-model="formInline.fastName" placeholder="苗字" clearable>
                <template slot="prepend">F</template>
              </el-input>
            </el-col>
            <el-col :span="6">
              <el-input v-model="formInline.lastName" placeholder="名前" clearable>
                <template slot="prepend">L</template>
              </el-input>
            </el-col>
          </el-row>
          <el-row :gutter="24" style="margin-top: 10px">
            <el-col :span="6" :offset="6">
              <el-input v-model="formInline.domain" placeholder="ドメイン名" clearable>
                <template slot="prepend">＠</template>
              </el-input>
            </el-col>
           </el-row>

        <el-row style="margin-top: 10px">
          <el-col :span="11">
            <el-button type="primary" plain @click="onSubmit" style="padding:15px 100px;float: right" :disabled="isLogin">スタート</el-button>
          </el-col>
          <el-col :span="2">&#12288;</el-col>
          <el-col :span="11" >
            <el-button type="warning" plain @click="deleteInfo" style="padding:15px 100px">リッセト</el-button>
          </el-col>
        </el-row>
        </el-main>
        <el-row :gutter="20" style="margin-top: 5px" v-loading="loading" element-loading-text="コーヒー飲んで来ても大丈夫ですよ">
          <el-col :span="4"><div>&#12288;</div></el-col>
          <el-col :span="16">
            <el-table
                    :data="tableData"
                    style="width: 100%">
              <el-table-column
                      prop="date"
                      label="日付"
                      width="180">
              </el-table-column>
              <el-table-column
                      prop="name"
                      label="パタン"
                      width="180">
              </el-table-column>
              <el-table-column
                      prop="address"
                      label="存在確認">
              </el-table-column>
            </el-table>
          </el-col>
          <el-col :span="4">&#12288;</el-col>
        </el-row>
      </el-main>
    </el-container>
  </el-container>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      status :true,
      formInline: {
        fastName: '',
        lastName: '',
        domain: ''
      },
      tableData: [{
        date: '2019-07-30',
        name: 'dawda@dada.com',
        address: 'false'
      }],
      loading: false,
      fits: 'fill',
      url: "https://fuss10.elemecdn.com/e/5d/4a731a90594a4af544c0c25941171jpeg.jpeg"
    }
  },
  computed:{
    isLogin(){
      if (this.formInline.fastName !== '' && this.formInline.lastName && this.formInline.domain){
        return this.status = false
      }else {
        return this.status = true
      }
    }
  },
  methods: {
    onSubmit() {
      console.log(this.formInline.fastName,this.formInline.lastName,this.formInline.domain)
      this.loading = true
    },
    deleteInfo(){
      this.formInline.fastName = "";
      this.formInline.lastName = "";
      this.formInline.domain = "";
      this.$message({
        message: 'リセットしました',
        type: 'success'
      });
    },
    open() {
      this.$alert('ターゲットの苗字と名前とドメイン名を入力してくだい、' +
              '検索終わるまで数分間時間かかる場合もありますので、ご了承ください', 'このツールの使い方', {
        confirmButtonText: '閉じる',
        // callback: action => {
        //   this.$message({
        //     type: 'info',
        //     message: `action: ${ action }`
        //   });
        // }
      });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .el-col {
    border-radius: 4px;
  }
  .bg-purple-dark {
    background: #99a9bf;
  }
  .bg-purple {
    background: #d3dce6;
  }
  .bg-purple-light {
    background: #e5e9f2;
  }
  .grid-content {
    border-radius: 4px;
    min-height: 36px;
  }
  .el-header {
    background-color: #409EFF;
    color: #333;
    line-height: 60px;
  }

  .el-aside {
    color: #333;
  }
</style>
