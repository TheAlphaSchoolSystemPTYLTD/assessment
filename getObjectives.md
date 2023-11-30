**getObjectives**
----
    Returns an array of structured academic reporting objectives in JSON format.

* **Version History:**

    Version | Description
    --- | --- |
    TASS v59.01 | New API endpoint released.

* **Version:**

    3

* **Permission:**

    Academic Reporting > Assessment Setup > Objectives > View

* **Method:**

    `GET | POST`

*  **Params:**

    Parameter Name | Type | Mandatory | Validations | Notes
    --- | :---: | :---: | --- | --- |
    res_year | integer | Yes | Must be provided.<br>Must be numeric.<br>Must be exactly 4 digits in size. | Year to get objectives for.
    res_period | integer | Yes | Must be provided.<br>Must be numeric.<br>Must not be greater than 2 digits in size. | Period to get objectives for.
    obj_code | string | No | If provided, must not be greater than 4 characters in length. | Specific objective code to retrieve.
    include_inactive | boolean | No | If provided, must be either <i>true</i> or <i>false</i>. | Default is <i>false</i>.<br>If set to <i>true</i> then inactive objectives will be included in the return results.

* **Success Response:**
    ```json
      {
        "data":
        [
          {
            "obj_desc": "Problem Solving",
            "active_flg": "Y",
            "obj_code": "PS1"
          },
        ],
        "__tassversion": "01.000.043.0",
        "token":
        {
          "res_year": 2023,
          "res_period": 1,
          "timestamp": "{ts '2023-11-29 13:44:01'}"
        }
      }
    ```
 
* **Error Response:**

    ```javascript
      __invalid:
      {
        "res_year": "Value must be provided."
      }
    ```

    ```javascript
      __invalid:
      {
        "res_year": "Value must be numeric."
      }
    ```

    ```javascript
      __invalid:
      {
        "res_year": "Value must be 4 digits."
      }
    ```

    ```javascript
      __invalid:
      {
        "res_period": "Value must be provided."
      }
    ```

    ```javascript
      __invalid:
      {
        "res_period": "Value must be numeric."
      }
    ```

    ```javascript
      __invalid:
      {
        "res_period": "Value must be 2 digits or less."
      }
    ```
	
    ```javascript
      __invalid:
      {
        "obj_code": "Value must be 4 characters or less."
      }
    ```
    
    ```javascript
      __invalid:
      {
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
