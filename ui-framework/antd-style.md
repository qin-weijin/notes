# Antd Style

- 兼容样式引擎
- 暗色模式一件切换
- 主题灵活扩展
- 复合样式 Stylish
- Ant Design Token Sys
- less 平滑迁移
- 响应式轻松适配
- 微应用良好兼容
- 应用案例

## API

createStyles

createStylish

createGlobalStyle

ThemeProvider

StyleProvide

useTheme

useThemeMode

useResponsive

setupStyled

createInstance

## cssinjs

@ant-design/cssinjs























```tsx
import { createStyles } from 'antd-style';
// css object 写法
const useStyles = createStyles(({ token, css }) => ({
  container: {
    backgroundColor: token.colorBgLayout,
    borderRadius: token.borderRadiusLG,
    maxWidth: 400,
    width: '100%',
    height: 180,
    display: 'flex',
    alignItems: 'center',
    justifyContent: 'center',
    flexDirection: 'column',
    marginLeft: 'auto',
    marginRight: 'auto',
  },
// 字符串写法
  card: css`
    color: ${token.colorTextTertiary};
    box-shadow: ${token.boxShadow};
    &:hover {
      color: ${token.colorTextSecondary};
      box-shadow: ${token.boxShadowSecondary};
    }

    padding: ${token.padding}px;
    border-radius: ${token.borderRadius}px;
    background: ${token.colorBgContainer};
    transition: all 100ms ${token.motionEaseInBack};

    margin-bottom: 8px;
    cursor: pointer;
  `,
}));
export default () => {

  const { styles, cx, theme } = useStyles();

  return (
    // cx 组织 className
    <div className={cx('a-simple-create-style-demo-classname', styles.container)}>
      <div className={styles.card}>createStyles Demo</div>
      {/* theme 对象包含了所有的 token 与主题等信息 */}
      <div>当前主题模式：{theme.appearance}</div>
    </div>
  );
};
```