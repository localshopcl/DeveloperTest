# **Developer Test for Localshop**

    Welcome!, in Localshop we are happy that you got into this stage and exited to know about your problem solving skills and your ability to learn fast, this document contains a series of questions and problems that we want to you to solve, you will have until 31 of december at 12:00 pm to deliver this test

    thank you for participating!
    Localshop Team
    
    ![](/assets/localshopBlack.png)

## **Questionarie**
### 1- Describe the process you have for a programming task(from requirements to delivery).
### 2- Databases are the most common way to storage data in complex aplications, these days are different types of them separated in relational databases(SQL) and non-relational databases explain the good vs bad about them and in wich case you will use one or another
### 3- Grab any invoice and create a database to store the data on it, create the entity diagram and database dictionary too
### 4- Someone ask you to create a webapp to chat with clients, this should support Whatsapp and Facebook Messenger, Which architecture and technologies will you use?(please add a diagraman in your answer)
### 5- What is your process to test and find bugs in an application?
### 6- What do you know about Cloud Computing?
### 7- What do you know about Agile software development process?
### 8- remember question number 3?. Create a query to obtain all data from the tables you create to store invoice data
### 9- Create a JSON with your personal data, include at least 1 object and 1 array
### 11- Finding errors is a good skill to have, please review the next code and tell us what is the problem, why the message is trigered before is intended? do the nessesary changes in the code to fix it


```javascript
const moment = require("moment-timezone")
const { db } = require("../../../firebase")

const getOpenedBusiness = async (dialogflowInfo) => {
  let intentResponse={};
  let closedBussiness = false;
  let merge_behavior;
  let textToRespond="";
  const chileTime = moment().tz('America/Santiago')
  const openAt = 10
  const monthDay = chileTime.format('MM-DD')
  const currentHourMinute = chileTime.format('hh:mm')
  const beforeOpenAt = chileTime.hour() < openAt
  

  intentResponse.merge_behavior ="APPEND";
  

  if((monthDay === "12-24" || monthDay ==="12-25" || monthDay === "12-31" || monthDay === "01-01")     && (chileTime.hour() >=19)){
    textToRespond=`¡Hola! 👋🏼\n\n\t\t A nombre de todo el Equipo de Localshop y en\n representación de todos los locales y shoppers que son\n parte de esta hermosa red, te damos las gracias por\n todo el apoyo que has entregado a la vida de barrio.\n\n\t\t En estas fiestas estaremos apoyándote en los\n siguientes horarios:\n\n- 24 Dic: 10:00 a 19:00 hrs\n- 25 Dic: Cerrado\n- 31 Dic: 10:00 a 19:00 hrs\n - 1 Enero : Cerrado \n\n ¡Te deseamos felices fiestas y que \n tengas un excelente 2021!`;
    intentResponse.merge_behavior = "REPLACE"
    closedBussiness=true
  }

  if (beforeOpenAt || currentHourMinute>="2030") {
      textToRespond=`¡Hola! 👋🏼\n\nGracias por comunicarte con Localshop. Tus tiendas de barrio volverán a recibir pedidos desde las 10:00 AM!\nPuedes dejar tu pedido escrito acá o elige directamente en www.localshop.cl y te escribiremos en la apertura para procesarlo.\n\n¡Gracias por cuidar la vida de barrio! 🏡`
      intentResponse.merge_behavior = "REPLACE"
      closedBussiness=true
  }
  
  
  intentResponse.textToRespond= textToRespond;
  intentResponse.session_info = {
    parameters: {
        closedBussiness: closedBussiness        
    }
  }
  
  return intentResponse
}

module.exports = getOpenedBusiness;
```




## **Challenge 1:** reactJS
    - create a simple reactJs app for adding products to a store
        - at least create and use 3 components
        - you can use mock data (JSON)
        - should be very simple but think about the UI/UX
        - create a github repo, upload your code and send us the link 
        - you are free to use any additional framework, library you want to


## **Challenge 2:** Chatbot
    - create a simple chatbot that answer frequent questions about become a Shopper, you can look for information in https://site.localshop.cl/TyC you can use any avaiable free tier tools from AWS, IBM, Microsoft or Google
        - let us know if you complete this challenge. We will contact you so we can test it



## delivery
    - send your test and any file necessary to cgarcia@localshop.cl

