**getResultFormats**
----
    Returns an array of structured academic reporting objectives in JSON format.

* **Version History:**

    Version | Description
    --- | --- |
    TASS v59.01 | New API endpoint released.

* **Version:**

    3

* **Permission:**

    Academic Reporting > Assessment Setup > Result Formats > View

* **Method:**

    `GET | POST`

*  **Params:**

    Parameter Name | Type | Mandatory | Validations | Notes
    --- | :---: | :---: | --- | --- |
    res_year | integer | Yes | Must be provided.<br>Must be numeric.<br>Must be exactly 4 digits in size. | Year to get objectives for.
    res_period | integer | Yes | Must be provided.<br>Must be numeric.<br>Must not be greater than 2 digits in size. | Period to get objectives for.
    rpt_type | string | No | If provided, must not be greater than 1 character in length. | Specific report type to retrieve.
    include_inactive_objectives | boolean | No | If provided, must be either <i>true</i> or <i>false</i>. | Default is <i>false</i>.<br>If set to <i>true</i> then inactive objectives will be included in the return results.

* **Success Response:**
    ```json
      {
        "data":
        [
          {
            "sub_code": "0100",
            "yr_level_desc": "DD",
            "yr_level": -5,
            "sub_desc": "Work Skills",
            "rpt_type": "A"
            "objectives":
            [
              {
                "obj_desc": "Writing",
                "active_flg": "Y",
                "assess_code": "S1",
                "obj_code": "WR"
              }
            ],
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
        "rpt_type": "Value must be 1 character or less."
      }
    ```
    
    ```javascript
      __invalid:
      {
        "include_inactive_objectives": "Value must be boolean."
      }
    ```
    
* **Sample Parameters:**

    ```javascript
      {
        "res_year": 2023, 
        "res_period": 1,
        "rpt_type": "A",
        "include_inactive_objectives": true
      }
    ```

* **Sample GET:** (With URL Encoded `token`)

    ```HTML
      http://api.tasscloud.com.au/tassweb/api/?method=GetResultFormats&appcode=API29&company=10&v=2&token=uWJx9ZdDOiF5tkxrwEZpZ%2FGPhCS4MrjeK4PE8QvYHjeQRH2LoYO6VYFVXkHn%2BGNA
    ```
  
* **Sample POST:**

    ```HTML
      <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
        <input type="hidden" name="method" value="getResultFormats">
        <input type="hidden" name="appcode" value="API29">
        <input type="hidden" name="company" value="10">
        <input type="hidden" name="v" value="3">
        <textarea name="token">uWJx9ZdDOiF5tkxrwEZpZ%2FGPhCS4MrjeK4PE8QvYHjeQRH2LoYO6VYFVXkHn%2BGNA</textarea>
      </form>
    ```
