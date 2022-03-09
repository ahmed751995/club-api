# The Club API

* the base url is the website url
* the header Authorization is an api key where
    * the key : Authorization
    * the value : token api_key:api_secret

## Renew Subscription

* [GET/Subscriptions]()

    * get a list of unpaid invoices of the __customer__ either they overdue
    or unpaid

* method: __GET__

* url: [{base url}/api/resource/Sales Invoice]()

* body: {form-data}
        
    | key           |        value  |
    | ------------- |---------------|
    | filters       | [["status", "=", "UnPaid"], ["customer", "=", "{Member name}"]] |
    | fields        | ["name", "grand_total"]     |


    * attributes: 
        
        __filter__ : on which the data will be filtered

        * Status: {'Unpain', 'Paid', 'Overdue'}
        * customer: {Member name}
    
        __fields__ : data fields on the response
        
        * name: the invoice name
        * grand_total: the invoice value
        
* Sample:
  
    ```bash
        curl --location --request GET '{base url}/api/resource/Sales Invoice' \
        --header 'Authorization: token token api_key:api_secret' \
        --form 'filters="[[\"status\", \"!=\", \"Paid\"], [\"status\", \"!=\", \"Cancelled\"], [\"customer\", \"=\", \"أحمد محمود أحمد محمد الببلاوي\"]]"' \
        --form 'fields="[\"name\", \"grand_total\"]"'
    ```

* response

    ```json
        {
            "data": [
                {
                    "name": "ACC-SINV-2022-00006",
                    "grand_total": 5000.0
                }
            ]
        }
    ```
    * data : list of total invoices
    


## Booking Academy
* [POST/new academy]()
    * book new academy for member or 
    
















