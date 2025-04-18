# 1. High Level Architecture Diagram

![Solution](HighLevel.png)

# 2. Screen Flow & ERD

## Screen Flow diagram
![Solution](ScreenFlow.png)

## ERD
![Solution](ERD.png)

# 3. API Design

API Design will be outline per services.

## Authorization Service

JWT authorization service.

## User Service



## Approval Service
Service responsible for keeping approval requests from both new account creation and new loans.

For the sake of simplicity, this service is a oversimplified service for marking requests

APIs as follows:

### POST /approvals

Create new approvals. newly created approval request is always PENDING

#### Request body
| Field Name| Type |Description |
| ----------- | ----------- | ---------|
| reference_id | string | reference id of the approval which refer to the original records
| type | ENUM (JPG, PDF, PNG) | type of the binary

Example:
```json
{
    "reference_id": "asdfasdf3534523453",
    "type": "LOAN"
}
```
#### Response body
| Field Name| Type |Description |
| ----------- | ----------- | ---------|
| id | string | approval id of the requested
| type | ENUM (ACCOUNT_OPENING, LOAN) | type of the requests
| reference_id | string | reference id of the approval which refer to the original records
| status | ENUM (ACCEPTED, REJECTED, PENDING) | status of the approval 

Example
```json
{
    "id": "asdfasdf3534523453",
    "reference_id": "asdfasdf3534523453",
    "status": "PENDING",
    "type": "LOAN"
}
```

### PATCH /approvals/accept/:id
Change status of the certain request to ACCEPTED. A request can only be accepted if the status is PENDING.

#### Request Path
| Field Name| Type |Description |
| ----------- | ----------- | ---------|
| id | string | id if the approval request

#### Response body
| Field Name| Type |Description |
| ----------- | ----------- | ---------|
| id | string | approval id of the requested
| type | ENUM (ACCOUNT_OPENING, LOAN) | type of the requests
| reference_id | string | reference id of the approval which refer to the original records
| status | ENUM (ACCEPTED, REJECTED, PENDING) | status of the approval 

Example
```json
{
    "id": "asdfasdf3534523453",
    "reference_id": "asdfasdf3534523453",
    "status": "ACCEPTED",
    "type": "LOAN"
}
```

### PATCH /approvals/reject/:id
Change status of the certain request to REJECTED. A request can only be accepted if the status is PENDING.

#### Request Path
| Field Name| Type |Description |
| ----------- | ----------- | ---------|
| id | string | id if the approval request

#### Response body
| Field Name| Type |Description |
| ----------- | ----------- | ---------|
| id | string | approval id of the requested
| type | ENUM (ACCOUNT_OPENING, LOAN) | type of the requests
| reference_id | string | reference id of the approval which refer to the original records
| status | ENUM (ACCEPTED, REJECTED, PENDING) | status of the approval 

Example
```json
{
    "id": "asdfasdf3534523453",
    "reference_id": "asdfasdf3534523453",
    "status": "REJECTED",
    "type": "LOAN"
}

### GET /approvals
get approval by parameter

#### Request parameter
| Field Name| Type |Description |
| ----------- | ----------- | ---------|
| reference_id | string | reference id of the approval which refer to the original records
| type | ENUM (ACCOUNT_OPENING, LOAN) | type of the requests

Example:
```text
GET/ reference_id?id=2342323&type=LOAN 
```

#### Response body
| Field Name| Type |Description |
| ----------- | ----------- | ---------|
| id | string | approval id of the requested
| type | ENUM (ACCOUNT_OPENING, LOAN) | type of the requests
| reference_id | string | reference id of the approval which refer to the original records
| status | ENUM (ACCEPTED, REJECTED, PENDING) | status of the approval 

Example
```json
{
    "id": "asdfasdf3534523453",
    "reference_id": "asdfasdf3534523453",
    "status": "PENDING",
    "type": "LOAN"
}
```

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

