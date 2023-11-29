**getResultYearsAndPeriods**
----
	Returns an array of structured result years and periods in JSON format.

* **Version History:**

  TASS v59.01 - New API endpoint.

* **Version:**

	3

* **Permission:**

	Academic Reporting > Assessment Setup > Result Periods > View

* **Method:**

	`GET | POST`

* **Params:**

	**Required:**

	n/a

	**Optional:**

	`res_year			[integer]`		If provided, only result years and periods matching the value will be returned.
	
	**Conditional:**

	n/a

* **Success Response:**
    ```json
      {
        "data": [
          {
            "res_period": 1,
            "semester": 2,
            "res_year": 2019,
            "archived_flg": "N",
            "prd_desc": "2019 Term 2",
            "rpt_type": "5"
		  },
        ],
        "__tassversion": "01.000.043.0",
        "token": {
			"res_year": 2019,
			"timestamp": "{ts '2023-11-29 13:44:01'}"
        }
      }
    ```
 
* **Error Response:**

    `res_year` is not numeric
    ```javascript
    __invalid: {
      "res_year": "Value must be numeric."
    }
    ```

    `res_year` must be 4 digits in size
    ```javascript
    __invalid: {
      "res_year": "Value must be 4 digits."
    }
    ```
    
* **Sample Parameters:**

  ```javascript
	{
		"res_year": 2019
	}
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?appcode=API29&v=3&method=GetResultYearsAndPeriods&token=Eh9N2jYqAAKMTKNgW7Tt3L%2FcMQafTfATA7gfcpGJ2Qw%3D&company=10
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getResultYearsAndPeriods">
       <input type="hidden" name="appcode" value="API29">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">Eh9N2jYqAAKMTKNgW7Tt3L/cMQafTfATA7gfcpGJ2Qw=</textarea>
    </form>
  ```
