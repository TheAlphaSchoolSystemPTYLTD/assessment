**getObjectives**
----
	Returns an array of structured academic reporting objectives in JSON format.

* **Version HIstory:**

  TASS v59.01 - New API endpoint.

* **Version:**

	3

* **Permission:**

  Academic Reporting > Assessment Setup > Objectives > View

* **Method:**

	`GET | POST`

*  **Params:**

	**Required:**

	`res_year			[integer]`		Year to get objectives for.
	
	`res_period			[integer]`		Period to get objectives for.

	**Optional:**

	`obj_code			[string]`		If provided, only an objective matching the value will be returned.
	
	`include_inactive		[boolean]`		Must be 'true' or 'false', default is 'false'. If set to 'true' then inactive objectives will be included in the returned data.

	**Conditional:**

	n/a

* **Success Response:**
    ```json
      {
        "data": [
          {
            "obj_desc": "Problem Solving",
            "active_flg": "Y",
            "obj_code": "PS1"
		  },
        ],
        "__tassversion": "01.000.043.0",
        "token": {
			"res_year": 2023,
			"res_period": 1,
			"timestamp": "{ts '2023-11-29 13:44:01'}"
        }
      }
    ```
 
* **Error Response:**

    `res_year` was not provided
    ```javascript
    __invalid: {
      "res_year": "Value must be provided."
    }
    ```

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

    `res_period` was not provided
    ```javascript
    __invalid: {
      "res_period": "Value must be provided."
    }
    ```

    `res_period` is not numeric
    ```javascript
    __invalid: {
      "res_period": "Value must be numeric."
    }
    ```

    `res_period` must be 2 digits or less in size
    ```javascript
    __invalid: {
      "res_period": "Value must be 2 digits or less."
    }
    ```
	
    `obj_code` must be 4 characters or less in size
    ```javascript
    __invalid: {
      "obj_code": "Value must be 4 characters or less."
    }
    ```
    
    `include_inactive` is not true or false
    ```javascript
    __invalid: {
      "include_inactive": "Value must be boolean."
    }
    ```
    
* **Sample Parameters:**

  ```javascript
	{
		"res_year": 2023, 
		"res_period": 1,
		"obj_code": "PS1",
		"include_inactive": true
	}
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=GetObjectives&appcode=API29&company=10&v=2&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We1Gqx9%2Fzb%2BcbVFartivsDN%2FxGgAIIjtABAYfzYPqTCpLf3gb0nW3h%2FTrPFLMhAdNcVvHD0Gz4FkRj5jRAD1aAGQ
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getObjectives">
       <input type="hidden" name="appcode" value="API29">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We1Gqx9/zb+cbVFartivsDN/xGgAIIjtABAYfzYPqTCpLf3gb0nW3h/TrPFLMhAdNcVvHD0Gz4FkRj5jRAD1aAGQ</textarea>
    </form>
  ```
