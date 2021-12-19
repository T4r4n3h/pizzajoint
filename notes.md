# To get started 
1. npm install framer-motion
2. import { motion } from 'framer-motion';
--**Note that I had to import {AnimatePresence, motion} from 'framer-motion/dist/framer-motion'instead for somereason that I dont know what!!
3. add motion. to the element tag you want to add the animation to the
4. add  **attribute** animate = {{
    property: value,
}}
## Initial values:
 * add **attribute** initial ={{prop:value}}
 this is how you can say where From 

## Transition:
* add **transition** transition={{prop:value}}
controlling how this animation works like easing-in duration, or delay the default is sprin but you could set it to inertia. "tween" is opposite fo bouncy.
** delay
** duration is when the type is 'tween'
** type:  default is "spring' can be changed to  'tween' 
** stiffness:  if type is spring the higher would be more stiffness (defualt is 100)
```
    initial={{x:'100vw'}}
    animate={{x:0}}
    transition={{type:'spring', delay:0.5}}
```

## Hover Effect
* replace the animate attribute with 'whileHover'
* make sure to set the **origin of the scale** (originx) to 0!
```
 whileHover={{ scale: 1.3, originX: 0, color: '#f8e112' }}
 transition={{ type: 'spring', stiffness: 300 }}
```
## Variants
* 1. extract our initial to a single outside to reference 
* 2. propagates changes to the Dom 
* 3. create timing relationships with the parents

above the component create a variable
```const containerVariants = {
  hidden:{
    opacity:0,
    x:'100vw'
  },
  visible:{
    opacity:1,
    x:0,
    transition:{type:'spring', delay:0.5}
  }
}
```
and then:
```
  <motion.div className="base container"
   variants={containerVariants}
   initial='hidden'
   animate='visible'
    transition={{type:'spring', delay:0.5}}
    >
```
* transition orchestration 
these are the properties that we define inside the transition property
** the (when) property
the spring type has 2 properties: 
```transition:{
      type:'spring',
      mass:0.4,
      damping:8,--> the oscillation of the spring the lower the damping the higher the swing
       when:'beforeChildren'}

  }
```
## Key Frames
 -    you can just put the properties in an array of values and it will bounce. 
 ```
    hover:{
    scale: [1, 1.1, 1, 1.1, 1, 1.1],
    textShadow: "0px 0px 8px rgb(255,255,255)",
    boxShadow: "0px 0px 8px rgb(255,255,255)",
    }
```
## Repeating Animation and no stop like a yoyo
    just add transition yoyo with the number of times you want the scale to yoyo like so:
```hover:{
    scale: 1.1,
    textShadow: "0px 0px 8px rgb(255,255,255)",
    boxShadow: "0px 0px 8px rgb(255,255,255)",
    transition: {
      duration:0.3,  
      yoyo:10
    }
```   
## Animate Present
we can set timeout to to change the state of something like with hooks!
 in order to animate something into a false state this can be done with 
 ```   
      <AnimatePresence>
        {showTitle &&(
          <motion.h2
          exit={{y:-1000}}
          >Thank you for your order :)</motion.h2>
        )}
      </AnimatePresence>
```
import it with motion from framer motion and use it
we also have to have exist animation as well as animate

1. to use it for the router you have to wrap the switch component with it 
2. theen let the animate know that it should exit before enter like so and then
3. use location should be imported form react dom and then create it inside the app 
check out lesson 12
```
import { Route, Switch, useLocation } from "react-router-dom";
```
