# CreateNode-project


## Installation
First create Folder Project
Create Folder Backend/Server
Move to Backend/Server directory
```bash
cd Backend  
```
or 
```bash
cd Server 
```
To create packege.json file run following command. 
```bash
npm init -y  
```
To install express, run following command. 
```bash
npm install express 
```
To use .env file run following command.
```bash
npm init dotenv 
```
To get body from request, run following command.
```bash
npm install body-parser
```
To install mongoose in project, run following command.
```bash
npm install mongoose
```
To install mongodb in project, run following command.
```bash
npm install mongodb
```
To auto start server install nodemon project, run following command.
```bash
npm install --save-dev nodemon 
```
Install all at once.
```bash
npm install express dotenv body-parser mongoose mongodb nodemon
```
Create .env file in Backend/Server folder to store enviornment variables in upper case.
```bash
 MONGODBURI=mongodb://localhost:27017/dbname
```
Create server.js/index.js file in Backend/Server folder.
  
Open packege.json replace this code 
```bash
 "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
```
with 
```bash
 "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
    "start":"node index.js"
    "dev":"nodemon index.js"
  },
```

create utils folder and create a file db.js and write this code
```bash
const mongoose=require('mongoose');
const URI=process.env.MONGODBURI;
const connectDB=async()=>{
try {
  const response=  await mongoose.connect(URI);
    if(response){
        console.log("MongoDB is Connected");
    }
    else{
        console.log("error while connecting" );
    }
} catch (error) {
    console.log("error while connecting MongoDB", error);
    process.exit(1);
}
}
module.exports=connectDB;
```
Open Server.js/index.js and paste this code
```bash
require('dotenv').config();
const express=require("express");
const app= express();
const connectDB= require("./Utils/db");
const  userRouter  = require('./Routes/userRoutes');
const port=5000;
app.use(express.json());
app.use("/api", userRouter)
connectDB().then(()=>{
    app.listen(port,()=>{
        console.log("Server is running on Port: ", port)
    })
})
```
Open Terminal and run the following command to run the project 
```bash
 npm run dev
```





