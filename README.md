# Python_webservices
Falcon python web services

<p align="center" width="100%">
    <img width="25%" src="https://github.com/jkaewprateep/Python_webservices/blob/main/Python.jpg">
    <img width="18.5%" src="https://github.com/jkaewprateep/Python_webservices/blob/main/Falcon.jpg">
    <img width="12.4%" src="https://github.com/jkaewprateep/Python_webservices/blob/main/cat_01.png">
    <img width="10.9%" src="https://github.com/jkaewprateep/Python_webservices/blob/main/ce6d14bd-9453-450b-a409-2558316d7e55.jpg"> </br> 
    <b> Create Python webserice with Falcon </b> </br>
    <b> ( Picture from Internet ) </b> </br>
</p>

🧸💬 Create a simple Python web service with Falcon, support HTTPS SSL, authentication methods, and Python library that runs with minimized resources. Possible for debugging and performing data analysis with many ready-to-use Python libraries. </br>
🐑💬 ➰ Python is not the fastest programming language running on complied code but is easy to implement user-friendly and adaptable, application is widely used in many areas including data science, research, and study, machine learning, adjustable display, and simulation. </br> 
🐐💬 Python and R-studio languages are more compatible when R-studio allows to perform some operation on dataset records by Python library or their library, implementation is simple when the build method is a famous way for data integration and communication. Do not forget to initial or remember ```__str__``` or ```__name__```is at the time value return and it may not equal or differently equal when step to next record or process task. This technique called ```instance variables``` allowed access to a value between processes without interrupts or method overriding. </br>

🐯💬 Culture INFO, should have only one name or one ```instance name``` because it is an expectation reason and you can have more than one or two integrated functions or you should perform by logit methods. </br>
🦭💬 The next technique is ```super itself``` when initial the class to prevent between ```instance variable values```, Python class same as the Java class they are store values they are running, and you may access the same way they are returned to connected invoking a method, prevent access of calculating value because it is between the value that might correct by some condition or rely on the application flow. </br>
🦁💬 As in many language ```dictionaries or enums``` are shared value then you do not need to initial or prevent multiple access because they are ready to use value but when num values export and use prohibited by using them without sources of reference they will be required comparing list and they are one evidence fast same as attendance sheet if we are looking at migration configuration problem ( data copyrights) as they are contained into one place. There are steps for clarification and improvement but it may take time and multiple methods to complete. One example is speech recognition companies or telephony network companies. </br>

```
import json
import falcon

##
from requests.models import PreparedRequest # for url params encoding
from dateutil import parser # for utc datetime phaser

##
import webrequest_methods;
import Alpaca_authen;
import Enums;
import MongoDB;

#
from bson.json_util import dumps;

class PositionModel(object) :
    def __init__(self, comingFrom):
        super().__init__();
        self.name = "PositionModel";
        self.authen = Alpaca_authen.authentication_struct( APCA_API_KEY_ID="******", APCA_API_SECRET_KEY="******" );
        self.webreqeusts = webrequest_methods.webrequest_methods();
        # self.orderenums = Enums.OrderEnums();
        self.mongoDB = MongoDB.MongoDBDatabase();
        return;
    
    def __str__ ():
        return "PositionModel";
        
    def on_get(self, req, resp):
        requester = req.context.auth["user"];

        resp.status = falcon.HTTP_200;
        response = dumps(self.getall_openpositions(self.authen));
        resp.text = response;
        resp.data = response; 
        self.mongoDB.insert_transactionlogging( req.headers, req.url, response, req.remote_addr, req.headers["USER-AGENT"], requester );

        return;

    def on_post(self, req, resp, symbol):
        requester = req.context.auth["user"];

        resp.status = falcon.HTTP_201;
        response = dumps(self.getan_openposition(symbol, self.authen));
        resp.text = response;
        resp.data = response;      
        self.mongoDB.insert_transactionlogging( req.headers, req.url, response, req.remote_addr, req.headers["USER-AGENT"], requester );
        return;

    def getan_openposition ( self, symbol, authen, url="https://paper-api.alpaca.markets/v2/positions"  ) :
        url = url + "/" + symbol;

        data = dict({ });
        params = dict({ });

        attributes=dict({});

        response_msg = self.webreqeusts.request_GET( data, params, authen, url);

        return response_msg
    
    def getall_openpositions ( self, authen, url="https://paper-api.alpaca.markets/v2/positions"  ) :

        data = dict({ });
        params = dict({ });

        attributes=dict({});

        listof_items = [['QCOM', '39be1334-06b6-4df2-a2f1-b21b942628d0'], ['SMCI', 'e4870680-5a31-43e0-a477-c47d158ac43d'], ['TSLA', '8ccae427-5dd0-45b3-b5fe-7ba5e422c766'], 
                        ['AMZN', 'f801f835-bfe6-4a9d-a6b1-ccbb84bfd75f'], ['GOOGL', '69b15845-7c63-4586-b274-1cfdfe9df3d8'], ['META', 'fc6a5dcd-4a70-4b8d-b64f-d83a6dae9ba4'], 
                        ['TQQQ', 'dce2ac30-c928-4416-be25-2213d057f30a'], ['AAPL', 'b0b6dd9d-8b9b-48a9-ba46-b9d54906e415'], ['AMD', '03fb07bb-5db1-4077-8dea-5d711b272625'], 
                        ['COIN', '1f3f7283-250d-4477-8b1e-037df55e5046'], ['CRWD', '26226278-b62c-47ec-a1bd-cf0dbd14b420'], ['SQQQ', 'cac38c1a-e01f-4d29-ab11-13c9c72991ce'], 
                        ['MSFT', 'b6d1aa75-5c9c-4353-a305-9e2caa1925ab'], ['MSTR', 'a9be5ee1-9ac7-4dbc-a09e-bb4ba98a3a19'], ['NFLX', 'bb2a26c0-4c77-4801-8afc-82e8142ac7b8'], 
                        ['NVDA', '4ce9353c-66d1-46c2-898f-fce867ab0247']];
        
        
        response_msg = [];
        for symbol, asset_id in listof_items :
            response_msg.append(self.getan_openposition(asset_id, self.authen));

        # response_msg = self.webreqeusts.request_GET( data, params, authen, url);

        return response_msg;
    
```
