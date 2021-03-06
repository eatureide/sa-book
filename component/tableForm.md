# TableForm

使用场景：
表格展示，筛选表格数据

```javascript
import React, { PureComponent } from 'react'
import { Input, Card, Button } from 'antd'
import TableForm from '@/components/TableForm'

function getData() {
  const data = Array(100).fill().map((_, index) => ({
    id: index,
    name: 'nickname' + index
  }))
  return new Promise((resolve, reject) => {
    resolve({
      code: 200,
      data: {
        array: data.slice(1, 1 * 1 + 10),
        total: data.length,
        count: 1,
        extras: {},
        offset: 0,
        page: 1,
        totalPageNo: data.length / 10
      }
    })
  })
}

class view extends PureComponent {

  componentRef = (ref) => {
    this._tableForm = ref
  }

  handleExportExcel = () => {
    /**
     * 有时候需要对组件进行操作，或者根据筛选参数导出excel，可以用ref获取到子组件的全部内容
     */
    const values = this._tableForm.handleGetFormValues() // 搜索框的值（经过处理的）
    const pages = this._tableForm.state.pageSearch // 页码
    console.log(values, pages)
  }

  render() {

    const tableFormProps = {
      request: getData, // 请求，返回promise，结果参考resolve的参数
      searchOptions: [ // 搜索选项，会生成一个form表单
        {
          itemProps: {
            label: '姓名', // label名
          },
          formItem: [
            {
              initialValue: '默认值', //输入框默认值
              valueName: 'name', // 值名
              node: <Input placeholder="请输入姓名" /> // 输入的组件
            }
          ]
        }
      ],
      columns: [ // 表格列，与Table组件参数一致
        {
          title: '姓名',
          dataIndex: 'name',
          key: 'name'
        },
      ],
      footerOptions: [ // 表格底部选项
        <Button onClick={ this.handleExportExcel }>导出excel</Button>
      ],
      otherOperating: [ // 搜索表单之外也许需要某些操作，如添加一些信息
        <Button type="primary">添加</Button>
      ],
      componentRef: this.componentRef // 操作子组件
    }

    return (
      <Card>
        <TableForm { ...tableFormProps } />
      </Card>
    )
  }
}

export default view
```

