<template>
  <div>
    <div id="department">
      <i class="el-icon-s-tools"></i>
      Department
    </div>
    <div id="tree">
      <el-tree
        :data="data"
        :props="defaultProps"
        @node-click="handleNodeClick"
      ></el-tree>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        data: [{
          label: 'All categories',
          children: [{
            label: 'T-shirt',
            children: [{
              label: 'Polo'
            }]
          }]
        }, {
          label: 'Electronic',
          children: [{
            label: 'Fans',
            children: [{
              label: 'Air conditions'
            }]
          }, {
            label: 'Chair',
            children: [{
              label: 'Love'
            }]
          }]
        }, {
          label: 'Clothing',
          children: [{
            label: 'Love',
            children: [{
              label: 'Love You'
            }]
          }, {
            label: 'I love you',
            children: [{
              label: 'Somuch'
            }]
          }]
        }],
        defaultProps: {
          children: 'children',
          label: 'label'
        }
      };
    },
    methods: {
      handleNodeClick(data) {
        console.log(data);
      }
    }
  };
</script>

<style scoped>
#department {
  border: 1px solid rgb(60, 60, 240);
  border-radius: 10px;
  color: rgb(60, 60, 240);
}
i {
  color: rgb(60, 60, 240);
}
</style>