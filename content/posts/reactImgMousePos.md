---
title: "Find out the position of the mouse over an image in React"
date: 2022-06-11T17:17:48-04:00
draft: false
---

1. Import the image and `useState` hook

   ```js
   import { useState } from "react";

   // exported the image from a index javascript file in assets
   import { waldoImg } from "./assets/index";
   ```

2. set the position as a state
   `const [position, setPosition] = useState([])`

3. create the `handleChange` function

   ```js
   // takes in an e
   const handleChange = (e) => {
     // provides information about the size of an element and its position relative to the viewport
     const bnds = e.target.getBoundingClientRect();

     // find the x and y position within the scope of the image (not the entire viewport)
     const x = e.clientX - bnds.left;
     const y = e.clientY - bnds.top;

     // set the state of the x and y
     setPosition([x, y]);
   };
   ```

4. show the image and the x and y coordinates
   ```js
   return (
     <div>
       <img
         alt="Where's Waldo"
         src={waldoImg}
         onMouseMove={(e) => handleChange(e)}
       />
       <div>x: {position[0]}</div>
       <div>y: {position[1]}</div>
     </div>
   );
   ```
