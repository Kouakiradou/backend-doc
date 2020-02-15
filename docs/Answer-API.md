# Answer API

## Get and add answer

### `POST` - api/addAnswer/

Use this request to upload a answer to databese



**Query Parameter(s)**:

None


**Request Body**:

```json
{
    "uid": "4fb2c7cf-e493-4aba-e5-3f3a3ae920ae",
    "date": "01/01",
    "age": "10",
    "questionAnswer": [
        {
            "qid": "1",
            "answerType": "text",
            "answer": "haha"
        }
    ]
}
```


#####answerContents

| Key        | Type      | Description                                             |
| ---------- | --------- | ------------------------------------------------------- |
| `uid`      | `string`  | Unique id for a questionnaire                        |
| `date`     | `string`  | The date when this answer is submited                           |
| `questionAnswer`   | `foreign key`  | answers for different questions                   |


#####questionAnswers

| Key        | Type      | Description                                             |
| ---------- | --------- | ------------------------------------------------------- |
| `qid`      | `string`  | Order id for a question                       |
| `answerType`     | `string`  | type of answer that is required, can be text or multiple choices                           |
| `answer`   | `string`  | the answer                   |


---

!!! success
    The answer is successfully submitted to database

    **Status Code**: `200 OK`

    **Response Body**:

    received


!!! failure "N/A"


### `Get` - api/getAnswerByUid/<str:id>/

Use this request to get a list of answer to questionnaire with the specified uid



**Query Parameter(s)**:

| Parameter  | Type     | Description                             |
| ---------- | -------- | --------------------------------------- |
| `uid`      | `string` | unique id for questionnaires            |

!!! note "Example"
    `api/getAnswerByUid/4fb2c7cf-e493-4aba-e5-3f3a3ae920ae/`


**Request Body**:

None


---

!!! success
    The user can be found using the query and have a full profile.

    **Status Code**: `200 OK`

    **Response Body**:

    ```json
    [
        {
            "uid": "4fb2c7cf-e493-4aba-e5-3f3a3ae920ae",
            "date": "01/01",
            "age": "10",
            "questionAnswer": [
                {
                    "qid": "1",
                    "answerType": "text",
                    "answer": "haha"
                }
            ]
        }
    ]
    ```


#####answerContents

| Key        | Type      | Description                                             |
| ---------- | --------- | ------------------------------------------------------- |
| `uid`      | `string`  | Unique id for a questionnaire                        |
| `date`     | `string`  | The date when this answer is submited                           |
| `questionAnswer`   | `foreign key`  | answers for different questions                   |


#####questionAnswers

| Key        | Type      | Description                                             |
| ---------- | --------- | ------------------------------------------------------- |
| `qid`      | `string`  | Order id for a question                       |
| `answerType`     | `string`  | type of answer that is required, can be text or multiple choices                           |
| `answer`   | `string`  | the answer                   |


!!! failure "get nothing"
    **Status Code**: `400 Bad Request`

    **Response Body**:

    get nothing