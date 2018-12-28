# belajar-react

### Daftar Isi
Satu
Dua
Tiga



### Instalasi

```bash
npx install create-react-app
npx creat-react-app myapp
```

### Introduction
### React Setup
### React Component
### State
```jsx
class App extends React.Component{
  state={
    name:'Ani',
    age: 30
  }
  render(){
    return(
      <div>
        <h4>My name is {this.state.name} and i am {this.state.age}</h4>
      </div>
    )
  }
}
```

### DOM Event
```jsx
class App extends React.Component{
  state={
    name:'Ani',
    age: 30
  }
  handleClick=(e)=>{
    console.log(this.state)
  }
  render(){
    return(
      <div>
        <h4>My name is {this.state.name} and i am {this.state.age}</h4>
        <button onClick={this.handleClick}>Click me</button>
      </div>
    )
  }
}
```
### Change State
### Forms
### Nesting Components
### Props
### Outputting List
### Stateless Component
### Conditional Output
### Forms
### Functions as props
### delete Data
### CSS
### Lifecycle Method
### React Router
### Link & NavLink
### Redirect
### HOC
### Axios
### Rooute Parameters
### Switch Tag
### Import Image
### Redux
### Map State to Props
### map Dispatch to props
### Action Creator
###


