**getAssessmentMethods**
----
    Returns an array of structured assessment methods and its associated validations in JSON format.

* **Version History:**

    Version | Description
    --- | --- |
    TASS v59.01 | New API endpoint released.

* **Version:**

    3

* **Permission:**

    Academic Reporting > Assessment Setup > Assessment Methods > View

* **Method:**

    `GET | POST`

*  **Parameters:**

    Parameter Name | Type | Mandatory | Validations | Notes
    --- | :---: | :---: | --- | --- |
    res_year | integer | Yes | Must be provided.<br>Must be numeric.<br>Must be exactly 4 digits in size. | Year to get assessment methods for.
    res_period | integer | Yes | Must be provided.<br>Must be numeric.<br>Must not be greater than 2 digits in size. | Period to get assessment methods for.
    assess_code | string | No | Must not be greater than 2 characters in length. | Specific assessment code to retrieve.

* **Success Response:**

    When an assessment method has a <i>'val_type'</i> of 'I' (individual), there could be one or more validations returned with the assessment method with the valid values provided in the <i>'valid_result'</i> field. <i>'min_val'</i> and <i>'max_val'</i> will be empty.

    ```json
      {
        "data": 
        [
          {
            "val_type": "I",
            "assess_desc": "Assessment Specific",
            "assess_code": "SW",
            "validations":      
            [
              {
                "valid_result": "A",
                "max_val": "",
                "min_val": ""
              },
              {
                "valid_result": "B",
                "max_val": "",
                "min_val": ""
              }
            ]
          },
        ],
        "__tassversion": "01.000.043.0",
        "token":
        {
          "res_year": 2017,
          "res_period": 1,
          "timestamp": "{ts '2023-11-29 13:44:01'}"
        }
      }
    ```

    When an assessment method has a <i>'val_type'</i> of 'R' (range), there will be exactly one validation returned with the assessment method with the min/max values provided in the <i>'min_val'</i> and <i>'max_val'</i> fields. <i>'valid_result'</i> will be empty.

    ```json
      {
        "data": 
        [
          {
            "val_type": "R",
            "assess_desc": "Assessment Range",
            "assess_code": "E4",
            "validations": 
            [
              {
                "valid_result": "",
                "max_val": "20",
                "min_val": "1"
              }
            ]
          }			
        ],
        "__tassversion": "01.000.043.0",
        "token":
        {
          "res_year": 2017,
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
	
    `assess_code` must be 2 characters or less in size
    ```javascript
    __invalid: {
      "assess_code": "Value must be 2 characters or less."
    }
    ```
    
* **Sample Parameters:**

    ```javascript
    {
      "res_year": 2017, 
      "res_period": 1,
      "assess_code": "E4"
    }
    ```

* **Sample GET:** (With URL Encoded `token`)

    ```HTML
      http://api.tasscloud.com.au/tassweb/api/?method=GetAssessmentMethods&appcode=API29&company=10&v=3&token=uWJx9ZdDOiF5tkxrwEZpZwL/KfzQay/sPYEa3tMW7FLWHz1+9mT9PJsVNmoq+l5X2enBUIMJk/aVlKdd9377jMCGSBa7CWmK7bp5zu71Ykw=
    ```
  
* **Sample POST:**

    ```HTML
      <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
        <input type="hidden" name="method" value="getAssessmentMethods**">
        <input type="hidden" name="appcode" value="API29">
        <input type="hidden" name="company" value="10">
        <input type="hidden" name="v" value="3">
        <textarea name="token">uWJx9ZdDOiF5tkxrwEZpZwL/KfzQay/sPYEa3tMW7FLWHz1+9mT9PJsVNmoq+l5X2enBUIMJk/aVlKdd9377jMCGSBa7CWmK7bp5zu71Ykw=</textarea>
    </form>
    ```
