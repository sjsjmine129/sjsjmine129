# get_product_option

## **API Endpoint**

- **URI**: **`/get_product_options/{product_id}`**
- **HTTP Method**: **`GET`**

## **Path Parameters**

- **product_id**: Integer. The unique identifier for the product whose options you want to retrieve.
    
    ```
    /get_product_options/4
    ```
    

## **Response**

### **Success**

- **HTTP Status Code**: **`200`**
- **Content-Type**: **`application/json`**

### Body

```json
jsonCopy code
{
  "success": true,
  "data": {
    "color": [
      {
        "option": "yellow",
        "additional_amount": null,
        "quantity": 10000,
        "is_deleted": false},
      {
        "option": "red",
        "additional_amount": 3000,
        "quantity": 3,
        "is_deleted": false}
    ]
  },
  "detail_code": "00",
  "message": "success get product info",
  "returnToken": "your-return-token-here"
}

```

### **Failure**

- **HTTP Status Code**: **`500`**
- **Content-Type**: **`application/json`**

### Body

```json
jsonCopy code
{
  "success": false,
  "detail_code": "00",
  "message": "SQL error",
  "returnToken": null}

```

---

## **Notes**

- The **`data`** field in the success response contains option details grouped by their category.
- The **`is_deleted`** field is a boolean indicating the status of the option.