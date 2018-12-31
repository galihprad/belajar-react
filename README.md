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
cara memanggil `state`
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
Jika ingin menambahkan DOMEvent berupa `onClick`, tambahkan fungsi baru `handleClick`
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
Jika ingin mengubah state, gunakan `this.setState()`
```jsx
class App extends React.Component{
  state={
    name:'Ani',
    age: 30
  }
  handleClick=(e)=>{
    this.setState({
      name: 'Anddy'
    })
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
### Basic Form
Jika ingin mengubah state berdasarkan input gunakan `onChange`
```jsx
class App extends React.Component{
  state={
    name:'Ani',
    age: 30
  }
  handleClick=(e)=>{
    this.setState({
      name: 'Anddy'
    })
    console.log(this.state)
  }
  handleChange=(e)=>{
     this.setState({
      name: e.target.value
     }
  }
  render(){
    return(
      <div>
        <h4>My name is {this.state.name} and i am {this.state.age}</h4>
        <button onClick={this.handleClick}>Click me</button>
        <form>
          <input type="text" onChange={this.handleChange}/>
        </form>
      </div>
    )
  }
}
```

untuk mensubmit sebuah form gunakan `onSubmit`
```jsx
class App extends React.Component{
  state={
    name:'Ani',
    age: 30
  }
  handleClick=(e)=>{
    this.setState({
      name: 'Anddy'
    })
    console.log(this.state)
  }
  handleChange=(e)=>{
     this.setState({
      name: e.target.value
     }
  }
  handleSubmit=(e)=>{
    e.preventDefault(); // Digunakan agar page tidak merefresh
    console.log('form dubmitted', this.state.name)
  }
  render(){
    return(
      <div>
        <h4>My name is {this.state.name} and i am {this.state.age}</h4>
        <button onClick={this.handleClick}>Click me</button>
        <form onSubmit={this.handleSubmit}>
          <input type="text" onChange={this.handleChange}/>
          <button>Submit</button>
        </form>
      </div>
    )
  }
}
```
### Nesting Components


Misalkan dimiliki file `App.js` dan `Profil.js`
Kita akan menesting component Profil.js ke App.js


Profil.js
```jsx
class Profil extends React.Component{
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

export default Profil
```
perhatikan `<Profil/>`
App.js
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
        <Profil/>
      </div>
    )
  }
}
```
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


