<template>
  <el-table :data='actList' style='width:100%' border>
    <el-table-column type='expand'>
      <template slot-scope='props'>
        <el-form label-position='left' label-width="100px">
          <el-form-item label='活动ID'>{{props.row.actID}}</el-form-item>
          <el-form-item label='活动主题'>{{props.row.theme}}</el-form-item>
          <el-form-item label='活动内容'>{{props.row.content}}</el-form-item>
          <el-form-item label='活动地点'>{{props.row.location}}</el-form-item>
          <el-form-item label='活动时间'>{{props.row.datetime}}</el-form-item>
          <el-form-item label='报名截止时间'>{{props.row.ddl}}</el-form-item>
          <el-form-item>
            <el-button @click="joinAct">加入活动</el-button>
          </el-form-item>
        </el-form>
      </template>
    </el-table-column>
    <el-table-column label='活动主题' prop='theme'></el-table-column>
    <el-table-column label='活动时间' prop='datetime'></el-table-column>
    <el-table-column label='地点' prop='location'></el-table-column>
  </el-table>
</template>
<script>
export default {
  data () {
    return {
      actList: [{
        actID: 1,
        theme: '自习',
        content: '一起学习',
        location: '二教',
        datetime: '2020-05-04 12:00',
        ddl: '2020-05-04 09:00'
      } , {
        actID: 2,
        theme: '篮球',
        content: '篮球走起',
        location: '五四篮球场',
        datetime: '2020-05-10 14:00',
        ddl: '2020-05-10 10:00'
      }],
      type: this.listtype
    }
  },
  props: ['listtype'],
  created: function () {
    if (listtype === 'all') {
      this.$axios({
        method: 'get',
        url: '/BackEnd/get_all_activities/',
      })
        .then(function (response) {
          console.log(response)
        })
    }
  }
}
</script>
<style>

</style>
