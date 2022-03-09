# The Club API

* the base url is the website url
* the header Authorization is an api key where
    * the key : Authorization
    * the value : token api_key:api_secret

## Subscriptions
members subscription

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
booking new academy for member, submember or not member

* [POST/new academy]()
   
    * book new academy for member, submember or not member 
    
* method: __POST__

* url: [{base url}/api/resource/Student Applicant]()

* body: {form-data}

    | key           |        value  |
    | ------------- |---------------|
    | data          | {data attributes} |
 


    __data attributes__

    | key                   | Description                                                        | value                                  |
    |-----------------------|--------------------------------------------------------------------|----------------------------------------|
    | customer              | Member named                                                       | Member named                           |
    | rent                  | unknown                                                            | Yes|No                                 |
    | rent_date             | unknown                                                            | YYYY-MM-DD                             |
    | first_name            | Member first name                                                  | Member first name                      |
    | middle_name           | member middle name                                                 | member middle name                     |
    | last_name             | member last name                                                   | member last name                       |
    | program               | the name of available program to which the member can subscript to | program name                           |
    | student_category      | the category of the member (Member, submember or Not a member)     | member category name                   |
    | lms_only              | unknown                                                            | 0 | 1                                  |
    | paid                  | unknown                                                            | 0 | 1                                  |
    | academic_year         | unknown                                                            | YYYY                                   |
    | academic_term         | the name of the sport to which the member wants to subscript to    | sport name                             |
    | student_admission     | unknow                                                             | name of student_admission              |
    | date_of_birth         | the Member birth date                                              | YYYY-MM-DD                             |
    | customer_gender       | the member gender                                                  | ذكر  |  انثي                           |
    | blood_group           | the member blood type                                              | A+ | A- | B+ | B- | O+ | O-| AB+ | AB- |
    | student_email_id      | Member email address                                               | email                                  |
    | student_mobile_number | Member mobile numer                                                | mobile number                           |
    | nationality           | the member nationality                                             | text                                   |
    | customer       | Member named                       | Member named      |
    | rent           | unknown                            | Yes|No            |
    | rent_date      | unknown                            | YYYY-MM-DD        |
    | first_name     | Member first name                  | Member first name |
    | address_line_1 | the member address                 | text              |
    | address_line_2 | the member second address (option) | text              |
    | pincode        | unknow                             | number            |
    | city           | the member city                    | text              |
    | state          | the member state                   | text              |



* response

    ```json
        {
        "data": {
                data attributes
            }
        }
    ```

* sample 

    ```bash
        curl --location --request POST '{base url}/api/resource/Student Applicant' \
        --header 'Authorization: token token api_key:api_secret' \
        --form 'data="{\"customer\": \"أحمد محمود أحمد محمد الببلاوي\", \"rent\": \"Yes\", \"rent_date\":\"2022-03-31\", \"first_name\":\"عبد اللطيف صبحى\", \"program\":\"برنامج ايجار ملعب\",  \"academic_term\":\"UFC Gym\", \"student_admission\":\"100\",  \"student_category\":\"عضو النادي - كبار\", \"paid\":\"1\", \"lms_only\": \"1\", \"blood_group\":\"A+\", \"customer_gender\":\"ذكر\", \"student_mobile_number\":\"12313\", \"address_line_1\":\"م 34 كمبوند المنتزه-جنوب الاحياء-6اكتوبر\", \"pin_code\":\"12332\", \"student_email_id\": \"student@elnady.com\"}"' \
        --form 'fields="[\"name\"]"'
    ```

    * response
    
        ```json
            {
            "data": {
                "name": "EDU-APP-2022-00007",
                "owner": "ahmed@datasofteg.com",
                "creation": "2022-03-09 12:53:27.448388",
                "modified": "2022-03-09 12:53:27.448388",
                "modified_by": "ahmed@datasofteg.com",
                "parent": null,
                "parentfield": null,
                "parenttype": null,
                "idx": 0,
                "docstatus": 0,
                "customer": "أحمد محمود أحمد محمد الببلاوي",
                "rent": "Yes",
                "rent_date": "2022-03-31",
                "first_name": "عبد اللطيف صبحى",
                "middle_name": null,
                "last_name": null,
                "program": "برنامج ايجار ملعب",
                "student_category": "عضو النادي - كبار",
                "lms_only": 1,
                "paid": 1,
                "naming_series": "EDU-APP-.YYYY.-",
                "application_status": "Applied",
                "application_date": "2022-03-09",
                "academic_year": "2021",
                "academic_term": "UFC Gym",
                "student_admission": "100",
                "image": null,
                "date_of_birth": null,
                "customer_gender": "ذكر",
                "gender": null,
                "blood_group": "A+",
                "student_email_id": "student@elnady.com",
                "student_mobile_number": "12313",
                "nationality": null,
                "address_line_1": "م 34 كمبوند المنتزه-جنوب الاحياء-6اكتوبر",
                "address_line_2": null,
                "pincode": null,
                "city": null,
                "state": null,
                "title": "عبد اللطيف صبحى",
                "amended_from": null,
                "doctype": "Student Applicant",
                "guardians": [],
                "siblings": []
                }
            }
        ```

