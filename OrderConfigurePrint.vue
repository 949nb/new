<template>
  <div id="product-select">
      <!--基本信息-->
    <Card class="card-print">
      <div class="title">
        <span class="vertical-line"></span><span style="color:#1e1e1e">基本信息</span>
      </div>
      <Form :label-width="130">
        <Row>
          <Col span="8">
            <FormItem label="产品代码:">
              <Input type="text" placeholder="查询的内容不存在或者未输入查询内容">
              </Input>
            </FormItem>
          </Col>
          <Col span="8">
            <FormItem label="参考产品代码:">
              <Input type="text" placeholder="查询的内容不存在或者未输入查询内容">
                <Icon type="ios-search" slot="suffix"></Icon>
              </Input>
            </FormItem>
          </Col>
        </Row>
      </Form>
    </Card>
      <!--投保单打印-->
    <Card class="card-print">
      <div class="title">
        <span class="vertical-line"></span><span style="color:#1e1e1e">投保单打印</span>
      </div>
      <span class="add-print-lists"><Icon type="ios-add-circle-outline"/>点击添加</span>
      <div>
        <Table border
               ref="selection"
               :columns="columns"
               :data="data"
               stripe="true"
               class="printTable"
               highlight-row
               ></Table>
      </div>
    </Card>
      <!--保单打印-->
    <Card class="card-print">
      <div class="title">
        <span class="vertical-line"></span><span style="color:#1e1e1e">保单打印</span>
      </div>
      <span class="add-print-lists"><Icon type="ios-add-circle-outline"/>点击添加</span>
      <div>
        <Table border
               ref="selection"
               :columns="columns"
               :data="data2"
               stripe="true"
               class="printTable"></Table>
      </div>
    </Card>
  </div>
</template>

<script>
export default {
  data () {
    return {
      // columns是表头的数据
      columns: [
        {
          type: 'selection',
          width: 60,
          align: 'center',
          title: '选择'
        },
        {
          title: '打印功能',
          key: 'print',
          align: 'center',
          render: (h,params) => {
            let arr949 = []
            for(let i=0;i<params.row.print.length;i++){
              let arr = params.row.print
              arr949.push(arr[i])
            }
            return h('Select',{
              attrs:{
                placeholder: params.row.print[0] === undefined ? "点击此处选择类别" : `${params.row.print[0]}`
              }
            },[
              arr949.map( item => {
                  return h("Option",{
                       props: {
                          value: item,
                          label: item
                       }
                  })
               })
            ])
          },

        },
        {
          title: '机构代码',
          key: 'mecCode',
          align: 'center',
          render: (h,params) => {
            return h("div",[
              h("Input",{
                attrs:{
                  type:'text'
                },
                style:{
                  textAlign: 'center',
                  marginRight: '5px',
                }
              },`${params.row.mecCode}`),
            ])
          },
        },
        {
          title: '参考产品',
          key: 'reference',
          align: 'center',
          render: (h,params) => {
            return h("div",[
              h("Input",{
                attrs:{
                  type:'text',
                },
                style:{
                  textAlign: 'center',
                  marginRight: '5px',
                  width: '65%'
                }
              },`${params.row.print}`),
              h("Button",{
                attrs:{
                  type: 'primary',
                  size: 'small',
                  ghost: ''
                },
                style:{
                  display: "inline-block"
                }
              },"查看")
            ])
          },
        },
        {
          title: '单证识别码',
          key: 'idCode',
          align: 'center',
          render: (h,params) => {
            return h("div",[
              h("Input",{
                attrs:{
                  type:'text'
                },
                style:{
                  textAlign: 'center',
                  marginRight: '5px',
                }
              },''),
            ])
          },
        },
        {
          title: '模版类型',
          key: 'tempType',
          align: 'center',
          render: (h,params) => {
            return h("div",[
              h("Input",{
                attrs:{
                  type:'text',
                },
                style:{
                  textAlign: 'center',
                  marginRight: '5px',
                  width: '65%'
                }
              },''),
              h("Button",{
                attrs:{
                  type: 'primary',
                  size: 'small',
                  ghost: ''
                },
                style:{
                  display: "inline-block"
                }
              },"查看")
            ])
          },
        },
      ],
      // data代表 表的数据,第一项 print为数组
      data: [
        {
          print:["打印投保单",2,3,4,5,6,7,8,9,0],
          mecCode: 'mecCode',
          reference:'reference',
          idCode:'idCode',
          tempType:"tempType",
          cellClassName: {
            name: 'demo-table-info-cell-name'
          }
        },
        {
          print: ["打印团单投保单",2,3,4,5,6],
          mecCode: '1212',
          reference:'123123123',
          idCode:'idCode',
          tempType:"tempType"
        },
        {
          print: "123",
          mecCode: '1212',
          reference:'123123123',
          idCode:'idCode',
          tempType:"tempType"
        },
      ],
      data2: [
        {
          print: ``,
          mecCode: '',
          reference:'123123123',
          idCode:'idCode',
          tempType:"tempType"
        },
        {
          print: "",
          mecCode: '1212',
          reference:'123123123',
          idCode:'idCode',
          tempType:"tempType"
        },
        {
          print: "",
          mecCode: '1212',
          reference:'123123123',
          idCode:'idCode',
          tempType:"tempType"
        },
        {
          print: ``,
          mecCode: '',
          reference:'123123123',
          idCode:'idCode',
          tempType:"tempType"
        },
        {
          print: "",
          mecCode: '1212',
          reference:'123123123',
          idCode:'idCode',
          tempType:"tempType"
        },
        {
          print: "",
          mecCode: '1212',
          reference:'123123123',
          idCode:'idCode',
          tempType:"tempType"
        },
        {
          print: ``,
          mecCode: '',
          reference:'123123123',
          idCode:'idCode',
          tempType:"tempType"
        },
        {
          print: "",
          mecCode: '1212',
          reference:'123123123',
          idCode:'idCode',
          tempType:"tempType"
        },
        {
          print: "",
          mecCode: '1212',
          reference:'123123123',
          idCode:'idCode',
          tempType:"tempType"
        },
      ]
    }
  }
}
</script>

<style lang="less" scoped>
  #product-select{
    .title{
      font-size: 14px;
      height: 38px;
      line-height: 36px;
      text-align: left;
      border-bottom: 1px solid #e5e5e5;
      margin-bottom: 28px;
      margin-top: 4px;
    }
    .card-print{
      margin-bottom: 10px;
      position: relative;
    }
  }
  .printTable{
    margin-bottom: 30px;
    border-left: 1px solid #E6E6E6;
  }
  .add-print-lists{
    color: #FC7E03;
    position: absolute;
    right: 17px;
    top: 46px;
    font-size: 13px;
    cursor: pointer;
  }
</style>

