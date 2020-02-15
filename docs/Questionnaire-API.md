# Questionnaire API

## Get, add, edit and delete questionniares

### `GET` - api/getQuestionnairesList/

Use this request to return titie and uid of all the questonnaire in a list in JSON.

<!-- !!! warning "Authorization"
    `none` -->


**Query Parameter(s)**:
None

!!! note "Example"
    `api/getQuestionnairesList/`





**Request Body**:
None


---

!!! success
    A list of json object will be returned

    **Status Code**: `200 OK`

    **Response Body**:

    ``` json
    [
      {
        "uid": "4fb2c7cf-e493-4aba-87e5-3f3a3ae920ae",
        "title": "New Questionnaire"
      }
      {
        "uid": "7asdadqf-skj7-iad1-2qa5-sdkaklp20aef",
        "title": "New Questionnaire 2"
      }
    ]
    ```

    | Key        | Type      | Description                                             |
    | ---------- | --------- | ------------------------------------------------------- |
    | `uid`      | `string`  | Unique id for each questionnaire                        |
    | `title`    | `string`  | The title for a questionnaire                           |


!!! failure "N/A"
    


### `GET` - api/getAllQuestionnaires/

Use this request to return all content of all the questonnaire in a list in JSON.

<!-- !!! warning "Authorization"
    `none` -->


**Query Parameter(s)**:
None

!!! note "Example"
    `api/getQuestionnairesList/`


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
        "uid": "4fb2c7cf-e493-4aba-87e5-3f3a3ae920ae",
        "title": "New Questionnaire",
        "minAge": 10,
        "maxAge": 12,
        "description": "",
        "patientType": "Inpatient",
        "questionnaireContent": [
            {
                "qid": "1",
                "questionText": "What is your name?",
                "answerType": "Text",
                "choices": ""
            },
        ]
      }
    ]
    ```
    #####questionnaire

    | Key        | Type      | Description                                             |
    | ---------- | --------- | ------------------------------------------------------- |
    | `uid`      | `string`  | Unique id for each questionnaire                        |
    | `title`    | `string`  | The title for a questionnaire                           |
    | `minAge`   | `integer`  | minimum age for attending the survey                   |
    | `maxAge`   | `integer`  | maximum age for attending the survey                   |
    | `description`   | `string` | Description for the questionnaire                   |
    | `patientType`    | `string` | The type of the patient filling the questionnaire  |
    | `questionnaireContent`    | `foreign key` | The content of the questionnaire, include all the questions |

    #####questionnaireContent

    | Key        | Type      | Description                                             |
    | ---------- | --------- | ------------------------------------------------------- |
    | `qid`      | `string`  | ordered id for each question                       |
    | `questionText`    | `string`  | The title for a question                        |
    | `answertype`   | `string`  | can be text or choices                   |
    | `choices`   | `string`  | will be all available choices if answer type is multiple-choices                   |

!!! failure "N/A"







### `GET` - api/getQuestionnaireByUid/<str:id>/

Use this request to return content of the questonnaire specifid by uid provided in JSON.



**Query Parameter(s)**:

| Parameter  | Type     | Description                             |
| ---------- | -------- | --------------------------------------- |
| `uid`      | `string` | unique id for questionnaire             |

!!! note "Example"
    `api/getQuestionnaireByUid/4fb2c7cf-e493-4aba-87e5-3f3a3ae920ae/`




---

!!! success
    The user can be found using the query and have a full profile.

    **Status Code**: `200 OK`

    **Response Body**:

    ```json
    {
      "uid": "4fb2c7cf-e493-4aba-87e5-3f3a3ae920ae",
      "title": "New Questionnaire",
      "minAge": 10,
      "maxAge": 12,
      "description": "",
      "patientType": "Inpatient",
      "questionnaireContent": [
        {
            "qid": "1",
            "questionText": "What is your name?",
            "answerType": "Text",
            "choices": ""
        },
        {
            "qid": "2",
            "questionText": "How old are you?",
            "answerType": "Text",
            "choices": ""
        }
      ]
    }
    ```

    #####questionnaire

    | Key        | Type      | Description                                             |
    | ---------- | --------- | ------------------------------------------------------- |
    | `uid`      | `string`  | Unique id for each questionnaire                        |
    | `title`    | `string`  | The title for a questionnaire                           |
    | `minAge`   | `integer`  | minimum age for attending the survey                   |
    | `maxAge`   | `integer`  | maximum age for attending the survey                   |
    | `description`   | `string` | Description for the questionnaire                   |
    | `patientType`    | `string` | The type of the patient filling the questionnaire  |
    | `questionnaireContent`    | `foreign key` | The content of the questionnaire, include all the questions |

    #####questionnaireContent

    | Key        | Type      | Description                                             |
    | ---------- | --------- | ------------------------------------------------------- |
    | `qid`      | `string`  | ordered id for each question                       |
    | `questionText`    | `string`  | The title for a question                        |
    | `answertype`   | `string`  | can be text or choices                   |
    | `choices`   | `string`  | will be all available choices if answer type is multiple-choices                   |


!!! failure "get nothing"
    **Status Code**: `400 Bad Request`

    **Response Body**:

    
    get nothing
    



### `POST` - api/addQuestionnaire/

Use this request to post a questionnaire to database.



**Query Parameter(s)**:
None

!!! note "Example"
    `api/addQuestionnaire/`


**Request Body**:


```json
    {
      "uid": "4fb2c7cf-e493-4aba-87e5-3f3a3ae920ae",
      "title": "New Questionnaire",
      "minAge": 10,
      "maxAge": 12,
      "description": "",
      "patientType": "Inpatient",
      "questionnaireContent": [
        {
            "qid": "1",
            "questionText": "What is your name?",
            "answerType": "Text",
            "choices": ""
        },
        {
            "qid": "2",
            "questionText": "How old are you?",
            "answerType": "Text",
            "choices": ""
        }
      ]
    }
```


#####questionnaire

  | Key        | Type      | Description                                             |
  | ---------- | --------- | ------------------------------------------------------- |
  | `uid`      | `string`  | Unique id for each questionnaire                        |
  | `title`    | `string`  | The title for a questionnaire                           |
  | `minAge`   | `integer`  | minimum age for attending the survey                   |
  | `maxAge`   | `integer`  | maximum age for attending the survey                   |
  | `description`   | `string` | Description for the questionnaire                   |
  | `patientType`    | `string` | The type of the patient filling the questionnaire  |
  | `questionnaireContent`    | `foreign key` | The content of the questionnaire, include all the questions |

  #####questionnaireContent

  | Key        | Type      | Description                                             |
  | ---------- | --------- | ------------------------------------------------------- |
  | `qid`      | `string`  | ordered id for each question                       |
  | `questionText`    | `string`  | The title for a question                        |
  | `answertype`   | `string`  | can be text or choices                   |
  | `choices`   | `string`  | will be all available choices if answer type is multiple-choices                   |

---

!!! success
    a Http response will be returned

    **Status Code**: `200 OK`

    **Response Body**:

    received

  
!!! failure "N/A"
    **Status Code**: `400 Bad Request`

    **Response Body**:




### `POST` - api/editQuestionnaireByUid/<str:id>

Use this request to return titie and uid of all the questonnaire in a list in JSON.

<!-- !!! warning "Authorization"
    `none` -->


**Query Parameter(s)**:

| Parameter  | Type     | Description                             |
| ---------- | -------- | --------------------------------------- |
| `uid`      | `string` | unique id for questionnaire             |

!!! note "Example"
    `api/editQuestionnaireByUid/4fb2c7cf-e493-4aba-e5-3f3a3ae920ae/`


**Request Body**:

```json
    {
      "uid": "4fb2c7cf-e493-4aba-87e5-3f3a3ae920ae",
      "title": "New Questionnaire",
      "minAge": 10,
      "maxAge": 12,
      "description": "",
      "patientType": "Inpatient",
      "questionnaireContent": [
        {
            "qid": "1",
            "questionText": "What is your name?",
            "answerType": "Text",
            "choices": ""
        },
        {
            "qid": "2",
            "questionText": "How old are you?",
            "answerType": "Text",
            "choices": ""
        }
      ]
    }
```

#####questionnaire

  | Key        | Type      | Description                                             |
  | ---------- | --------- | ------------------------------------------------------- |
  | `uid`      | `string`  | Unique id for each questionnaire                        |
  | `title`    | `string`  | The title for a questionnaire                           |
  | `minAge`   | `integer`  | minimum age for attending the survey                   |
  | `maxAge`   | `integer`  | maximum age for attending the survey                   |
  | `description`   | `string` | Description for the questionnaire                   |
  | `patientType`    | `string` | The type of the patient filling the questionnaire  |
  | `questionnaireContent`    | `foreign key` | The content of the questionnaire, include all the questions |

  #####questionnaireContent

  | Key        | Type      | Description                                             |
  | ---------- | --------- | ------------------------------------------------------- |
  | `qid`      | `string`  | ordered id for each question                       |
  | `questionText`    | `string`  | The title for a question                        |
  | `answertype`   | `string`  | can be text or choices                   |
  | `choices`   | `string`  | will be all available choices if answer type is multiple-choices                   |


---

!!! success
    The user can be found using the query and have a full profile.

    **Status Code**: `200 OK`

    **Response Body**:

    edited


!!! failure "N/A"
    **Status Code**: `400 Bad Request`

    **Response Body**:



### `GET` - api/deleteQuestionnaireByUid/<str:id>



**Query Parameter(s)**:

| Parameter  | Type     | Description                             |
| ---------- | -------- | --------------------------------------- |
| `uid`      | `string` | unique id for questionnaire             |

!!! note "Example"
    `api/deleteQuestionnaireByUid/4fb2c7cf-e493-4aba-87e5-3f3a3ae920ae`


**Request Body**:
None



---

!!! success
    The questionnaire specified in parameter will be removed from database.

    **Status Code**: `200 OK`

    **Response Body**:

    deleted


!!! failure "Questionnaire not exist"
    **Status Code**: `400 Bad Request`

    **Response Body**:


    Questionnaire not exist 



