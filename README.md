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

  render(){
    return(
      <div>
        
      </div>
    )
  }
}

export default Profil
```
perhatikan `<Profil/>` dan `import Profil from './Profil'`

App.js
```jsx
import Profil from './Profil'

class App extends React.Component{

  render(){
    return(
      <div>
        <Profil/>
      </div>
    )
  }
}
```
### Props
Akan ditambahkan 2 buah props pada `<Profil/>` yaitu `name` dan `age`

App.js
```jsx
import Profil from './Profil'

class App extends React.Component{
  render(){
    return(
      <div>
        <Profil name="Andi" age="25"/>
      </div>
    )
  }
}
```
lalu kedua buah props tersebut dapat diakses di `Profil.js` dengan cara `this.props`

Profil.js
```jsx
class Profil extends React.Component{

  render(){
    return(
      <div>
        Name:{this.props.name}
        Age:{this.props.age}
      </div>
    )
  }
}

export default Profil
```
### Outputting List
bagaimana jika `props` nya banyak data?

Semisal di `App.js` sebagai berikut:
```jsx
import Profil from './Profil'

class App extends React.Component{
  state={
    profils:[
    {name: 'Ani', age: 30, id:1},
    {name: 'Adi', age: 20, id:2},
    {name: 'Ari', age: 25, id:3},
    ]
  }
  render(){
    return(
      <div>
        <Profil profils={this.state.profils}>
      </div>
    )
  }
}
```
terdapat array `state={profils:[...]}` yang akan kita pakai sebagai `props`. 

Lalu array tersebut dipanggil dengan `<Profil profils={this.state.profils}>`

Lalu di `Profil.js` array tersebut akan dikeluarkan menggunakan `map`:
```jsx
class Profil extends React.Component{

  render(){
    const{ profils }=this.props;
    const profilList=profils.map(
      profil=>{
        <div key={profil.id}>
          Name:{profil.name}
          Age:{profil.age}
        </div>
      }
    )
    return(
      <div>
        { profilList }
      </div>
    )
  }
}

export default Profil
```
pada `Profil.js` tersebut dibuat const baru  `profilList`.

Setiap data akan dikeluarkan satu persatu menggunakan `map`

Lalu dioutput menggunakan `{profilList}`

> **Note**: setiap hasil `map` harus memiliki `key` yang unik, sebagai contoh, bisa digunakan `id`


### Stateless Component
terdapat 2 jenis component pada React JS, yaitu Continer component dan UI Component

Cotainer Component:
* contain state
* contain lifecycle hooks
* not concern with UI
* use classes

UI component
* not contain state
* receive data from props
* concern with UI
* use function to create

Container component

```jsx
class Profil extends React.Component{

  render(){
    const{ profils }=this.props;
    const profilList=profils.map(
      profil=>{
        <div key={profil.id}>
          Name:{profil.name}
          Age:{profil.age}
        </div>
      }
    )
    return(
      <div>
        { profilList }
      </div>
    )
  }
}

export default Profil
```
UI component
```jsx
const Profil =(props)=>{
    const{ profils }=props;
    const profilList=profils.map(
      profil=>{
        <div key={profil.id}>
          Name:{profil.name}
          Age:{profil.age}
        </div>
      }
    )
    return(
      <div>
        { profilList }
      </div>
    )
  
}

export default Profil
```

### Conditional Output
### Forms 
```jsx
class AddProfil extends Component{
  state={
    name: null,
    age: null,
  }
  
  //untuk mengeset nilai state agar sama dengan isi form
  handleChange=(e)=>{    
    this.setState({
      [e.target.id]:e.target.value
    })
  }
  
  //nilai yg di disubmit akan dikeluarkan di console
  handleSubmit=(e)=>{
    e.preventDefault();
    console.log(this.state);
  }
  render(){
    return(
      <div>
        <form onSubmit={this.handleSubmit}>
          <label htmlFor="name">Name :</label>
          <input type="text" id="name" onChange={this.handleChange}/>
          <label htmlFor="age">Age :</label>
          <input type="text" id="age" onChange={this.handleChange}/>
          <button>Submit</button>
         </form>
      </div>
    )
  }
  
  export default AddProfil
  
```
### Functions as props
kita dapat menurunkan function berupa props, 
atau untuk memanggil props dari child ke parrent,
```jsx
class App extends Component{
  state={
    profils:[
      {name: 'Andi', age='20'},
      {name: 'Anti', age='30'}
    ]
  }
  
  //fungsi ini akan diturunkan sebagai props
  addProfil=(profil)=>{
  
     //id digenerate secara random saja biar gampang
    profil.id=Math.random(); 
    
     // mencopy setiap elemen di array profils, ke array baru
    let profils=[...this.state.profils, profil]
    
    this.setState({
      profils=profils
    })
  }
  render(){
    return(
      <div className="App">
        <Profils profils={this.state.profil}/>
        <AddProfil addProfil={this.addProfil} />
      </div>
    )
  }

}

```
fungsi `addProfil` diturunkan sebagai props

```jsx
class AddProfil extends Component{
  state={
    name: null,
    age: null,
  }
  
  //untuk mengeset nilai state agar sama dengan isi form
  handleChange=(e)=>{    
    this.setState({
      [e.target.id]:e.target.value
    })
  }
  
  //nilai yg di disubmit ke App.js
  handleSubmit=(e)=>{
    e.preventDefault();
    this.props.addProfil(this.state)
  }
  render(){
    return(
      <div>
        <form onSubmit={this.handleSubmit}>
          <label htmlFor="name">Name :</label>
          <input type="text" id="name" onChange={this.handleChange}/>
          <label htmlFor="age">Age :</label>
          <input type="text" id="age" onChange={this.handleChange}/>
          <button>Submit</button>
         </form>
      </div>
    )
  }
  
  export default AddProfil
  
```

hasil submit akan dipanggil di `App.js`

### delete Data
ditambahkan fungsi `deleteProfil` pada `App.js`, lalu diturunkan sebagai props, 

digunakan fungsi `filter` untuk mendelete data

App.js
```jsx
class App extends Component{
  state={
    profils:[
      {name: 'Andi', age='20'},
      {name: 'Anti', age='30'}
    ]
  }
  
  //fungsi ini akan diturunkan sebagai props
  addProfil=(profil)=>{
  
     //id digenerate secara random saja biar gampang
    profil.id=Math.random(); 
    
     // mencopy setiap elemen di array profils, ke array baru
    let profils=[...this.state.profils, profil]
    
    this.setState({
      profils=profils
    })
  }
  
  deleteProfil=(id)=>{
    let profils=this.state.profils.filter(profil=>{
      return profil.id! == id
    });
    this.setState({
      profils=profils
    })
  }
  render(){
    return(
      <div className="App">
        <Profils deleteProfil={this.deleteProfil} profils={this.state.profil}/>
        <AddProfil addProfil={this.addProfil} />
      </div>
    )
  }

}

```
lalu pada `Profil.js` ditambahkan button untul delete
```jsx
const Profil =(props)=>{
    const{ profils, deleteProfil }=props;
    const profilList=profils.map(
      profil=>{
        <div key={profil.id}>
          Name:{profil.name}
          Age:{profil.age}
          <button onClick={()=>{deleteNinja(ninja.id)}}></button>
          // diberi ()=> agar tidak selalu terpanggil otomatis
        </div>
        
      }
    )
    return(
      <div>
        { profilList }
      </div>
    )
  
}

export default Profil
```

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


