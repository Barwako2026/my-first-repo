# API Reference Entry: Create a New Task

## Endpoint
POST /projects/{projectId}/tasks

## Description
Creates a new task within the specified project. The task is created by the authenticated user, who is automatically recorded as its creator. On success, the endpoint returns the newly created task, including a system-generated ID and timestamps.

## Request Parameters

### Path Parameters
| Name | Type | Required | Description |
|---|---|---|---|
| projectId | string | Required | The unique identifier of the project the task belongs to. |

### Query Parameters
None.

### Body Parameters
| Name | Type | Required | Description |
|---|---|---|---|
| title | string | Required | The task's title. Must be 1–200 characters. |
| description | string | Optional | Additional detail about the task. If omitted, defaults to null. |
| assigneeId | string | Required | The user ID of the person the task is assigned to. |
| dueDate | string (ISO 8601 date, YYYY-MM-DD) | Required | The date the task is due. |
| priority | string (enum: low, medium, high) | Required | The task's priority level. |

## Request Headers
| Header | Value | Required |
|---|---|---|
| Authorization | Bearer <access_token> | Required — identifies the authenticated user. |
| Content-Type | application/json | Required. |

## Response Codes
| Code | Meaning |
|---|---|
| 201 Created | The task was created successfully. Response body contains the new task. |
| 400 Bad Request | The request body is malformed, missing a required field, or contains an invalid value (e.g. an invalid priority or malformed dueDate). |
| 401 Unauthorized | The Authorization header is missing, expired, or invalid. |
| 403 Forbidden | The authenticated user does not have permission to create tasks in this project. |
| 404 Not Found | The specified projectId does not exist, or the assigneeId does not correspond to a valid user. |
| 422 Unprocessable Entity | The request is well-formed JSON but fails business validation (e.g. dueDate is in the past). |
| 500 Internal Server Error | An unexpected server error occurred while processing the request. |

## Example Request

POST /projects/proj_8841/tasks
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
Content-Type: application/json

```json
{
  "title": "Design landing page mockup",
  "description": "Create a Figma mockup for the new landing page, focusing on the hero section and CTA placement.",
  "assigneeId": "user_2291",
  "dueDate": "2026-10-05",
  "priority": "high"
}
```

## Example Successful Response (201 Created)

```json
{
  "id": "task_57391",
  "projectId": "proj_8841",
  "title": "Design landing page mockup",
  "description": "Create a Figma mockup for the new landing page, focusing on the hero section and CTA placement.",
  "assigneeId": "user_2291",
  "dueDate": "2026-10-05",
  "priority": "high",
  "status": "open",
  "createdBy": "user_1043",
  "createdAt": "2026-09-22T09:15:32Z",
  "updatedAt": "2026-09-22T09:15:32Z"
}
```