**setStudentSubjectResults**
----
    Allows a list of student subject assessment results to be added / updated.

* **Version History:**

    Version | Description
    --- | --- |
    TASS v59.01 | New API endpoint released.

* **Version:**

    3

* **Permission:**

    Academic Reporting > Upload Academic Results

* **Method:**

    `GET | POST`

*  **Parameters:**

    Parameter Name | Type | Mandatory | Validations | Notes
    --- | :---: | :---: | --- | --- |
    res_year | integer | Yes | Must be provided.<br>Must be numeric.<br>Must be exactly 4 digits in size. | Year to apply subject assessment results for.
    res_period | integer | Yes | Must be provided.<br>Must be numeric.<br>Must not be greater than 2 digits in size. | Period to apply subject assessment results for.
    student_results | array | Yes | Must be provided. | List of student results to update.
    [student_results].stud_code | string | Yes | Must be provided.<br>Must not be greater than 8 characters in length. | Student code.
    [student_results].sub_code | string | Yes | Must be provided.<br>Must not be greater than 15 characters in length. | Subject code.
    [student_results].obj_code | string | Yes | Must be provided.<br>Must not be greater than 4 characters in length. | Objective code.
    [student_results].stud_result | string | Yes | Must be provided.<br>Must not be greater than 7 characters in length. | Assessment result.

* **Success Response:**

    ```json
      {
        "data":
        {
          "errors": [],
          "updatedRecords": 1
        },
        "__tassversion": "01.000.043.0",
        "token":
        {
          "res_period": 1,
          "timestamp": "{ts '2023-11-30 11:55:10'}",
          "res_year": 2023,
          "overwrite_existing_data": true
          "student_results":
          [
            {
              "sub_code": "0001",
              "stud_code": "0009642",
              "stud_result": 12,
              "obj_code": "ACH"
            }
          ],
        }
      }
    ```

* **Error Response:**

    The <i>line_number</i> property in the return errors array relates to the index position of the input record in the provided student_results array.

    ```json
    {
      "__status": "invalid",
      "data":
      {
        "errors":
        [
          {
            "line_number": 1,
            "messages":
            [
              "Results are already recorded for student assessment."
            ],
          }
        ],
        "updatedRecords": 0
      },
      "__tassversion": "01.000.043.0",
      "__invalid": {},
      "__locks": {},
      "token":
      {
        "res_period": 1,
        "timestamp": "{ts '2023-11-30 11:54:55'}",
        "res_year": 2023,
        "overwrite_existing_data": true
        "student_results":
        [
          {
            "sub_code": "0001",
            "stud_code": "0009642",
            "stud_result": 15,
            "obj_code": "ACH"
          }
        ],
      }
    }
    ```
 
* **Error Response:**

    ```javascript
    __invalid: {
      "res_year": "Value must be provided."
    }
    ```

    ```javascript
    __invalid: {
      "res_year": "Value must be numeric."
    }
    ```

    ```javascript
    __invalid: {
      "res_year": "Value must be 4 digits."
    }
    ```

    ```javascript
    __invalid: {
      "res_period": "Value must be provided."
    }
    ```

    ```javascript
    __invalid: {
      "res_period": "Value must be numeric."
    }
    ```

    ```javascript
    __invalid: {
      "res_period": "Value must be 2 digits or less."
    }
    ```
	
    ```javascript
    __invalid: {
      "student_results": "Value must be provided."
    }
    ```
    
* **Sample Parameters:**

  ```javascript
  {
    "res_year": 2023,
    "res_period": 1,
    "overwrite_existing_data": false,
    "student_results":
    [
      {
        "stud_code": "0009642",
        "sub_code": "0001",
        "obj_code": "ACH",
        "stud_result": "12"
      }
    ]
  }
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=SetStudentSubjectResults&appcode=API29&company=10&v=3&token=uWJx9ZdDOiF5tkxrwEZpZ7bCmBgXc8+ohGUkvMU9tTfLvbP8V750wG9Ud5mCq/ffCOIpJ5RIoacjluX5Qgde4AYiOqTXZzL0LoHR2mUuN70NNR1wYxQQeYDyPeqirusSfyAsR534FuPBfWUZEDmQYSxFDg2lDKyeFWnJTymmZdZ2nEAP/LSGP4e7VwG8HayNIt92J6uH/LxTUC2yq8Z4tD0ow3oFXfd0uFGPjxnJiWcdZNpehYQezstq1ioudRoVKUJkZ1xTCHHHq1eTxtgkmw==
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="setStudentSubjectResults**">
       <input type="hidden" name="appcode" value="API29">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">uWJx9ZdDOiF5tkxrwEZpZ7bCmBgXc8+ohGUkvMU9tTfLvbP8V750wG9Ud5mCq/ffCOIpJ5RIoacjluX5Qgde4AYiOqTXZzL0LoHR2mUuN70NNR1wYxQQeYDyPeqirusSfyAsR534FuPBfWUZEDmQYSxFDg2lDKyeFWnJTymmZdZ2nEAP/LSGP4e7VwG8HayNIt92J6uH/LxTUC2yq8Z4tD0ow3oFXfd0uFGPjxnJiWcdZNpehYQezstq1ioudRoVKUJkZ1xTCHHHq1eTxtgkmw==</textarea>
    </form>
  ```
