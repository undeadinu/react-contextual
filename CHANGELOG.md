## 3.4.0

* moduleContext

    Creates a global module-scoped context object and injects it both as `this.props.context` into the wrapped component, as well as `Component.Context`, so consumers can import the component and readily use it:

    ```js
    import { moduleContext } from 'react-contextual'

    @moduleContext()
    class Theme extends React.PureComponent {
        render() {
            const { context: Context, children } = this.props
            return <Contest.Provider value="red" children={children} />
        } 
    }

    @subscribe(Theme.Context, theme => ({ theme }))
    class Header extends React.PureComponent {
        render() {
            return <h1 style={{ color: theme }}>hello</h1>
        }
    }
    ```