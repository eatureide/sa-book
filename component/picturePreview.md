# PicturePreview

使用场景：
查看大图

```javascript
import React from 'react'
import { Card } from 'antd'
import PicturePreview from '@/components/PicturePreview'

export default function view() {
  return (
    <Card>
      <PicturePreview src="https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png" />
    </Card>
  )
}

```