import './App.css';
import React,{ useState } from 'react';
import Navbar from '../src/Navbar';
import TextForm from '../src/TextForm';
import Alert from '../src/Alert';
import About from './About';

import {
  BrowserRouter as Router,
  Switch,
  Route,
  Link
} from "react-router-dom";


function App() {
  const [mode, setMode] = useState ('light');
  const [alert,setAlert] =useState ('null');
   const showAlert=(message,type)=>{
    setAlert({
      msg: message,
      type: type
    })
    setTimeout(() => {
      showAlert(null);
    }, 3000);

   }
   const toggleMode =()=>{
    if(mode ==='dark'){
       setMode ('light');
       document.body.style.backgroundColor ='white';
       showAlert("Light has been enabled", "success");
        document.title ="TextUtils - Light Mode";
       }
       else{
        setMode ('dark');
        document.body.style.backgroundColor ='grey';
        showAlert("Dark has been enabled", "success");
         document.title ="TextUtils - Dark Mode";
       }
  }

  return (
    <>
   <Router>
<Navbar tittle="TextUtils" mode={mode} toggleMode= {toggleMode}/>
<Alert alert={alert}/>
<div className="container my-3">
<Switch>
          <Route exact path="/about">
            <About />
          </Route>
          <Route exact path="/">
          <TextForm showAlert={showAlert}heading="Enter  the text to analyze below" mode={mode}/>
          </Route>
        </Switch>
        </div>

        </Router>




</>
  );
}

export default App;
# TextUtils
