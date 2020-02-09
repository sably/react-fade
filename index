import {useState, useEffect, forwardRef, useRef, useImperativeHandle} from 'react';
import React from 'react';
import ReactDOM from "react-dom";
import "./style.css"

const App = (props) => {
    const [mountStyle, setMonutStyle] = useState({style: {opacity: 0, transition: 'all 1s ease'}})
    const [show, setToggle] = useState(props.mounted);
    
    useEffect(
        () => {
            setMonutStyle(
                (obj) => ({style: {...obj.style, opacity: props.mounted ? .75 : 0}})
            );
            props.mounted && setToggle(X => props.mounted)

            return console.log('unmounted');
        }, [props.mounted]);

    function transitionEndHandle() {
        !props.mounted && setToggle(x => !x);
    }

    return (show || (!show && props.mounted)) &&
        <div onTransitionEnd={transitionEndHandle} style={mountStyle.style} className={"fade"}></div>
}

const Parent = () => {
    const [showChild, setToggle] = useState(true)

    function buttonClick() {
        setToggle(x => !x)
    }

    return (<div>
        <App mounted={showChild}/>
        <button onClick={buttonClick} className={"fixed"}>{showChild ? 'Unmount' : 'Mount'}</button>
    </div>)


}

ReactDOM.render(<Parent/>, document.getElementById('root'))
