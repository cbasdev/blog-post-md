# How to use Multiple Layouts in NextJS (Typescript)

In the development of web applications, one of the fundamental aspects is the visual structure that it presents to the user. It's common to think of packaging our application with a specific layout, but what happens when we want to make it dependent on a route or a specific parameter of the view?

The NextJS documentation offers an interesting solution for the use of multiple layouts, but in this article we want to show an alternative where Layouts are not sent by props, but orchestrated directly in a main layout.

To achieve this, the first thing is to extend the AppProps type so that it receives an additional parameter, which will allow us to determine the layout to use in each view of the application.

```tsx
// _app.tsx

type ComponentWithPageLayout = AppProps & {
  Component: AppProps['Component'] & {
    PageLayout?: string
  }
}
```

Now, we package the entire application in a Layout and pass as a prop the layoutType we received from Component.PageLayout

```tsx
// _app.tsx 

export default function MyApp({ Component, pageProps }: ComponentWithPageLayout) {
  return (
    <Layout layoutType={Component.PageLayout}>
      <Component {...pageProps} />
    </Layout>
  )
}
```


Then we define the component that will be in charge of orchestrating the layouts


```tsx
// layout.tsx

import DefaultLayout from './FirstLayout'
import SecondLayout from './SecondLayout'

interface ILayout {
  children: JSX.Element
  layoutType?: string
}

interface ILayoutOptions {
  [key: string]: ({ children }: ILayout) => JSX.Element
}

const layouts: ILayoutOptions = {
  SecondLayout,
  '*': DefaultLayout,
}

function Layout({ children, layoutType }: ILayout) {
  const layoutSelected = layoutType ? layoutType : '*'
  const LayoutDefined = layouts[layoutSelected]
  return <LayoutDefined>{children}</LayoutDefined>
}

export default Layout
```

This allows us to dynamically define the available layouts in an object.

The way to use the Layout on a specific page would be:

```tsx
// pages/login.tsx

const Login = () => {
  return ...
}

Login.PageLayout = 'SecondLayout'
export default Login
```

In summary, there are several ways to handle layouts in a web application, and in this article we have presented an alternative where layouts are directly orchestrated in a main layout and entire components are not shipped by props, allowing more control over the layout.
