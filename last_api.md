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
        
    | key     | value                                                           |
    |---------|-----------------------------------------------------------------|
    | filters | [["status", "=", "UnPaid"], ["customer", "=", "{Member name}"]] |
    | fields  | ["name", "grand_total"]                                         |


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

    | key                   | Description                                                        | value                           |
    |-----------------------|--------------------------------------------------------------------|---------------------------------|
    | customer              | Member named (in case he is a member)                              | Member named                    |
    | rent                  | unknown                                                            | Yes  or  No                     |
    | rent_date             | unknown                                                            | YYYY-MM-DD                      |
    | first_name            | Member first name                                                  | Member first name               |
    | middle_name           | member middle name                                                 | member middle name              |
    | last_name             | member last name                                                   | member last name                |
    | program               | the name of available program to which the member can subscript to | program name                    |
    | student_category      | the category of the member (Member, submember or Not a member)     | member category name            |
    | lms_only              | unknown                                                            | 0 or 1                          |
    | paid                  | unknown                                                            | 0 or 1                          |
    | academic_year         | unknown                                                            | YYYY                            |
    | academic_term         | the name of the sport to which the member wants to subscript to    | sport name                      |
    | student_admission     | unknow                                                             | name of student_admission       |
    | date_of_birth         | the Member birth date                                              | YYYY-MM-DD                      |
    | customer_gender       | the member gender                                                  | ذكر  or   انثي                  |
    | blood_group           | the member blood type                                              | A+   A- B+  B-  O+  O-  AB+  AB |
    | student_email_id      | Member email address                                               | email                           |
    | student_mobile_number | Member mobile numer                                                | mobile number                   |
    | nationality           | the member nationality                                             | text                            |
    | customer              | Member named                                                       | Member named                    |
    | rent                  | unknown                                                            | Yes or No                       |
    | rent_date             | unknown                                                            | YYYY-MM-DD                      |
    | first_name            | Member first name                                                  | Member first name               |
    | address_line_1        | the member address                                                 | text                            |
    | address_line_2        | the member second address (option)                                 | text                            |
    | pincode               | unknow                                                             | number                          |
    | city                  | the member city                                                    | text                            |
    | state                 | the member state                                                   | text                            |



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


## change email

change member or submember email address email address

* [PUT/email]()
        
    * update member email address
        
* method: __PUT__
    
* url : {base url}/api/resource/Address/{member name}
    
    ** member name: member or submember name  

* body: {form-data}

    | key  | value                                     |
    |------|-------------------------------------------|
    | data | {"email_id":"{member new email address}"} |
    
    * email_id : member or submember new email address 
    
* sample:

    ```bash
	curl --location --request PUT '{base url}/api/resource/Address/حلا حسنى كسبه-ابناء' \
	--header 'Authorization: token token api_key:api_secret' \
	--form 'data="{\"email_id\":\"hala@gmail.net\"}"'
    ```
    
    * response
    
    ```json
        {
        "data": {
            "name": "حلا حسنى كسبه-ابناء",
            "owner": "Administrator",
            "creation": "2021-12-19 18:36:38.463383",
            "modified": "2022-03-09 14:46:48.501842",
            "modified_by": "ahmed@datasofteg.com",
            "parent": null,
            "parentfield": null,
            "parenttype": null,
            "idx": 0,
            "docstatus": 0,
            "member_no": "1172",
            "main_member": "1172",
            "full_name": "حلا حسنى كسبه",
            "customer_group": "عضو تابع",
            "yearly_fees_": 150.0,
            "personal_identification_number": "31204160102643",
            "id_member": null,
            "address_title": "حلا حسنى كسبه",
            "address_type": "ابناء",
            "address_line1": "بدون",
            "date_of_birth": "2009-07-20",
            "image": "/files/1172-3.jpg",
            "address_line2": null,
            "city": "جيزة",
            "county": null,
            "state": null,
            "country": "Egypt",
            "pincode": null,
            "email_id": "hala@gmail.net",
            "phone": null,
            "fax": null,
            "tax_category": null,
            "is_primary_address": 0,
            "is_shipping_address": 0,
            "disabled": 0,
            "is_your_company_address": 0,
            "doctype": "Address",
            "links": [
                {
                    "name": "7dd50df69f",
                    "owner": "Administrator",
                    "creation": "2021-12-19 18:36:38.463383",
                    "modified": "2022-03-09 14:46:48.501842",
                    "modified_by": "ahmed@datasofteg.com",
                    "parent": "حلا حسنى كسبه-ابناء",
                    "parentfield": "links",
                    "parenttype": "Address",
                    "idx": 1,
                    "docstatus": 0,
                    "link_doctype": "Customer",
                    "link_name": "1172",
                    "link_title": "أ.د.حسني حامد حسني كسبه",
                    "doctype": "Dynamic Link"
                }
            ]
        },
        "_server_messages": "[\"{\\\"message\\\": \\\"File /files/1172-3.jpg does not exist\\\"}\"]"
        }
	```


## Information

### get main member information

* [GET/member]()


* method: __GET__

* url: [{base url}/api/resource/Customer]()

* body: {form-data}

    | key     | value                                                                                                       |
    |---------|-------------------------------------------------------------------------------------------------------------|
    | fields  | ["name", "mobile_no",  "customer_group", "personal_identification_number", "release_date2", "expiry_date2"] |
    | filters | [["name", "=", "{customer name}"]]                                                                          |
    |         |                                                                                                             |

	* attributes: 
        
		__filter__ : on which the data will be filtered

	* name: {Member name}
    
		__fields__ : data fields on the response
        
		* name: the member name
		* mobile_no: the member mobile number
		* customer_group: the member type
		* personal_identification_number: membership number
		* release_date2: the membership release date
		* release_date2: the membership renew date
		
* sample

	```bash
	curl --location --request GET '{base url}/api/resource/Customer' \
	--header 'Authorization: token token api_key:api_secret' \
	--form 'fields="[\"name\", \"mobile_no\",  \"customer_group\", \"personal_identification_number\", \"release_date2\", \"expiry_date2\"]"' \
	--form 'filters="[[\"name\", \"=\", \"وليد شعبان محسن راضي\"]]"'
	```
	
	* response
	
	```json
		{
		"data": [
			{
				"name": "وليد شعبان محسن راضي",
				"mobile_no": "1002016587",
				"customer_group": "عضوية عاملة",
				"personal_identification_number": "28310152104078",
				"release_date2": "2022-03-10",
				"expiry_date2": "2022-03-14"
			}
			]
		}
	```
	
	


### get submember information

* [GET/member]()

* method: __GET__

* url: {base url}/api/resource/Address

* body: {form-data}

    | key     | value                                                                                     |
    |---------|-------------------------------------------------------------------------------------------|
    | fields  | ["main_member","full_name", "phone",  "customer_group", "personal_identification_number"] |
    | filters | [["full_name", "=", "{Member full name}"]]                                                |

    * attributes: 
        
	__filter__ : on which the data will be filtered
		
	* full_name: {Member full name}
    
	__fields__ : data fields on the response
        
	* main_member: main member's  membership number
	* full_name: the member full name
	* mobile_no: the member mobile number
	* customer_group: the membership type
	* personal_identification_number: membership number
	(hint: release date and expiry date the same as main member date)

* sample:

  ```bash
	  curl --location --request GET  {base url}/api/resource/Address' \
	  --header 'Authorization: token token api_key:api_secret' \
	  --form 'fields="[\"main_member\", \"full_name\", \"phone\",  \"customer_group\", \"personal_identification_number\"]"' \
	  --form 'filters="[[\"full_name\", \"=\",\"لى لى عبداللطيف صبحى\"]]"'
  ```

	* respose
	
	```json
		{
		"data": [
			{
				"main_member": "102",
				"full_name": "لى لى عبداللطيف صبحى",
				"phone": null,
				"customer_group": "عضو تابع",
				"personal_identification_number": "31101140600384"
			}
			]
		}
	```
