**MobSF REST APIs**

1. `api/v1/upload` - [Upload a File](#upload-file-api)
2. `api/v1/scan` - [Scan a File](#scan-file-api)
3. `api/v1/delete_scan` - [Delete a Scan](#delete-scan-api)
4. `api/v1/download_pdf` - [Download PDF Report](#generate-pdf-report-api)


**Upload File API**
----
API to upload a file. Supported file types are apk, zip, ipa and appx.

* **URL:** `/api/v1/upload`

* **Method:** `POST`
  
*  **Data Params**

Param Name | Param Value | Required
---------- | ----------- | --------
file | `multipart/form-data` | Yes

* **Success Response:**

  * **Code:** `200` <br />
    **Content-Type:**  `application/json; charset=utf-8` <br />
    **Content:** `{"file_name": "diva-beta.apk", "hash": "82ab8b2193b3cfb1c737e3a786be363a", "scan_type": "apk"}`
 
* **Error Response:**

  * **Code:**  `500 Internal Server Error` or  `405 Method Not Allowed` or `422 Unprocessable Entity` <br />
    **Content-Type:**  `application/json; charset=utf-8` <br />
    **Content:** `{"error": <error message> }`

  OR

  * **Code:** `401 Unauthorized` <br />
    **Content-Type:**  `application/json; charset=utf-8` <br />
    **Content:** `{"error": "You are unauthorized to make this request." }`

* **Sample Call:**

  ```
  curl -F 'file=@/Users/ajin/Desktop/diva-beta.apk' http://localhost:8000/api/v1/upload
  ```
<hr>

**Scan File API**
----
API to scan a file that is already uploaded.

* **URL:** `/api/v1/scan`

* **Method:** `POST`
  
*  **Data Params**


Param Name | Param Value | Required
---------- | ----------- | --------
scan_type | apk, zip, ipa, or appx | Yes
file_name | Name of the app with extension | Yes
hash | hash of the scan | Yes
re_scan | 0 or 1, default is 0 | No


* **Success Response:**

  * **Code:** `200` <br />
    **Content-Type:**  `application/json; charset=utf-8` <br />
    **Content:** 
   ```
   {"act_count": "17", "api": {"Loading Native Code (Shared Library) ": {"path": 
   ["jakhar/aseem/diva/DivaJni.java"]}, "Local File I/O Operations": {"path": 
   ["jakhar/aseem/diva/InsecureDataStorage2Activity.java", "jakhar/aseem/diva/SQLInjectionActivity.java"]}, 
   "Starting Activity": {"path": ["jakhar/aseem/diva/AccessControl1Activity.java", 
   "jakhar/aseem/diva/AccessControl2Activity.java", "jakhar/aseem/diva/AccessControl3Activity.java", 
   "jakhar/aseem/diva/MainActivity.java"]}, "Query Database of SMS, Contacts etc.": {"path": 
   ["jakhar/aseem/diva/AccessControl3NotesActivity.java", "jakhar/aseem/diva/NotesProvider.java"]}
   SNIPPED
   ```
 
* **Error Response:**

  * **Code:**  `500 Internal Server Error` or  `405 Method Not Allowed` or `422 Unprocessable Entity` <br />
    **Content-Type:**  `application/json; charset=utf-8` <br />
    **Content:** `{"error": <error message> }`

  OR

  * **Code:** `401 Unauthorized` <br />
    **Content-Type:**  `application/json; charset=utf-8` <br />
    **Content:** `{"error": "You are unauthorized to make this request." }`

* **Sample Call:**

  ```
  curl -X POST --url http://localhost:8000/api/v1/scan --data "scan_type=apk&file_name=diva-
  beta.apk&hash=82ab8b2193b3cfb1c737e3a786be363a"
  ```

<hr>

**Delete Scan API**
----
API to delete scan results.

* **URL:** `/api/v1/delete_scan`

* **Method:** `POST`
  
*  **Data Params**

Param Name | Param Value | Required
---------- | ----------- | --------
hash | hash of the scan | Yes

* **Success Response:**

  * **Code:** `200` <br />
    **Content-Type:**  `application/json; charset=utf-8` <br />
    **Content:** `{"deleted": "yes"}` or `{"deleted": "no"}`

* **Error Response:**

  * **Code:**  `500 Internal Server Error` or  `405 Method Not Allowed` or `422 Unprocessable Entity` <br />
    **Content-Type:**  `application/json; charset=utf-8` <br />
    **Content:** `{"error": <error message> }`

  OR

  * **Code:** `401 Unauthorized` <br />
    **Content-Type:**  `application/json; charset=utf-8` <br />
    **Content:** `{"error": "You are unauthorized to make this request." }`

* **Sample Call:**

  ```
  curl -X POST --url http://localhost:8000/api/v1/delete_scan --data "hash=82ab8b2193b3cfb1c737e3a786be363a"
  ```
<hr>

**Generate PDF Report API**
----
API to generate PDF Report

* **URL:** `/api/v1/download_pdf`

* **Method:** `POST`
  
*  **Data Params**

Param Name | Param Value | Required
---------- | ----------- | --------
hash | hash of the scan | Yes
scan_type| apk, andzip, ioszip, ipa, or appx | Yes

* **Success Response:**

  * **Code:** `200` <br />
    **Content-Type:**  `application/pdf` <br />
    **Content:** `PDF Contents`

* **Error Response:**

  * **Code:**  `500 Internal Server Error` or  `405 Method Not Allowed` or `422 Unprocessable Entity` <br />
    **Content-Type:**  `application/json; charset=utf-8` <br />
    **Content:** `{"error": <error message> }`

  OR

  * **Code:** `401 Unauthorized` <br />
    **Content-Type:**  `application/json; charset=utf-8` <br />
    **Content:** `{"error": "You are unauthorized to make this request." }`

* **Sample Call:**

  ```
  curl -X POST --url http://localhost:8000/api/v1/download_pdf --data "hash=82ab8b2193b3cfb1c737e3a786be363a&scan_type=apk"
  ```