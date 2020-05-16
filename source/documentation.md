--- 

title: PlanetTerp API 

language_tabs: 
   - shell 

toc_footers: 
   - <a href='#'>Sign Up for a Developer Key</a> 
   - <a href='https://github.com/lavkumarv'>Documentation Powered by lav</a> 

includes: 
   - errors 

search: true 

--- 

# Introduction 

PlanetTerp API 

**Version:** 1 

# /COURSES
## ***GET*** 

**Summary:** Get courses

**Description:** Get all courses, in alphabetical order

### HTTP Request 
`***GET*** /courses` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| department | query | Only get courses in a department. Must be four characters. | No |  |
| reviews | query | Show reviews for the course (reviews for professors that taught the course and listed this course as the one being reviewed) | No |  |
|  |  |  | No |  |
|  |  |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Returns courses matching query |
| 400 | bad input parameter |

# /PROFESSORS
## ***GET*** 

**Summary:** Get professors

**Description:** Get all professors, in alphabetical order

### HTTP Request 
`***GET*** /professors` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| type | query | Show only reviews for professors or teaching assistants | No |  |
| reviews | query | Show reviews for the professor | No |  |
|  |  |  | No |  |
|  |  |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Returns professors matching query |
| 400 | bad input parameter |

# /GRADES
## ***GET*** 

**Summary:** Get grades

**Description:** Get grades for a course, professor, or both.

### HTTP Request 
`***GET*** /grades` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| course | query | Show only grades for the given course | No |  |
| professor | query | Show only grades for the given professor | No |  |
| semester | query | Show only grades for the given semester. Semester should be provided as the year followed by the semester code. `01` means Spring and `08` means Fall. For example, `202001` means Spring 2020. | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Returns grades matching query |
| 400 | bad input parameter |

<!-- Converted with the swagger-to-slate https://github.com/lavkumarv/swagger-to-slate -->
