# Ant Design of Vue Components

- Button 
- Icon
- Typography
- Affix
- FloatButton
- Watermark

布局

- Divider
- Flex
- Grid
- Layout
- Space

导航

- Anchor
- Breadcrumb
- Dropdown
- Menu
- PageHeader
- Pagination
- Steps

数据录入

数据展示

反馈

## App or ConfigProvider

**App**

- 提供静态方法 `message.xxx`、`Modal.xxx`、`notification.xxx`
- 提供 CSS Reset

**ConfigProvider**

- autoInsertSpaceInButton

```vue
<a-config-provider 
  :theme="{ 
    token: { ... }
  }">
  <a-app>...</a-app>
</a-config-provider>

const { message, modal, notification } = App.useApp()
const showMessage = () => { 
  message.success('Success!'); 
};
```
