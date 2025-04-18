# 1. High Level Architecture Diagram

![Solution](HighLevel.png)

# 2. Screen Flow & ERD

## Screen Flow diagram
![Solution](ScreenFlow.png)

## ERD
![Solution](ERD.png)

# 3. API Design

API Design will be outline perservices.

## Authorization Service

## User Service

## Approval Service

## File Service

Service responsible to hold file links to third-party hosting services or raw form of files like pdf or texts.

APIs as follows:

### POST /files
Create file record

#### Request body
| Field Name| Type |Description |
| ----------- | ----------- | ---------|
| raw | string | raw binary of the files
| type | ENUM (JPG, PDF, PNG) | type of the binary

Example:
```json
{
    "raw": "asdfasdf3534523453",
    "type": "JPG"
}
```

#### Response body
| Field Name| Type |Description |
| ----------- | ----------- | ---------|
| file_id | string | the record file id register in the database

Example
```json
{
    "id": "asdfasdf3534523453"
}
```

### GET /file

#### Request parameter
| Field Name| Type |Description |
| ----------- | ----------- | ---------|
| id | string | file id of the requested
| type | ENUM (JPG, PDF, PNG) | type of the binary

Example:
```text
GET/ file?id=2342323&type=JPG 
```

#### Response body
| Field Name| Type |Description |
| ----------- | ----------- | ---------|
| id | string | file id of the requested
| type | ENUM (JPG, PDF, PNG) | type of the binary
| raw | string | raw binary of the files

Example
```json
{
    "id": "asdfasdf3534523453",
    "raw": "asdfasdf3534523453",
    "type": "JPG"
}
```

### Loan Service



## 4. Screen Flow Detail

![Solution](ScreenFlowDetail.png)

