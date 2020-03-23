# PictureUpload

使用场景：
表单所需（本组件既可以使用自身的state，也可以与Form表单联动状态），使用亚马逊AWS-S3作为上传，进度条因sdk不支持的原因，所以是假load



```javascript
import React, { PureComponent } from 'react'
import PictureUpload from '@/components/PictureUpload'
import { Button, Form } from 'antd'

class view extends PureComponent {

  handleGetRefValue = () => {
    //获取上传后的url数组
    console.log(this.refs.pictureUpload.state.fileList)
  }

  handleGetFormValue = () => {
    const values = this.props.form.getFieldsValue()
    console.log(values)
  }

  render() {
    const { getFieldDecorator } = this.props.form
    return (
      <>
        <a href="https://www.npmjs.com/package/aws-s3">sdk文档</a>
        <Form>
          <Form.Item>
            {
              getFieldDecorator('img')(
                <PictureUpload
                  maxLength={ 1 } //图片上传个数
                  maxSize={ 1 } //图片大小限制（mb）
                />
              )
            }
          </Form.Item>
        </Form>
        <Button onClick={ this.handleGetFormValue }>getFormValue</Button>
        <PictureUpload ref="pictureUpload" />
        <Button onClick={ this.handleGetRefValue }>getRefValue</Button>
      </a>
    )
  }
}

export default Form.create()(view)
```