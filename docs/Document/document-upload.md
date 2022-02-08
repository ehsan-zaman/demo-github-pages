---
layout: default
title: Document Upload
parent: Document
has_toc: true
nav_order: 1
---

# Document Upload
{: .no_toc }

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

This endpoint is for uploading document for further tasks like validating the document, inviting the signers, check the status of the document and downloading the document.

## Endpoint

<table>
  <tbody>
    <tr>
      <td>Path</td>
      <td>/api/document/upload.json</td>
    </tr>
    <tr>
      <td>Method</td>
      <td>POST</td>
    </tr>
    <tr>
      <td>Request Body Schema</td>
      <td>application/json</td>
    </tr>
  </tbody>
</table>

## Request Body Parameter Description

| Key          |  Requirement | Type            | Description                                                                                                             |
| :---         |  :---        | :---            | :---                                                                                                                    |
| access_token |  Mandatory   | String          | API Access Token                                                                                                        |
| access       |  Mandatory   | String          | Document access. Possible values: public, private                                                                       |
| file         |  Mandatory   | Object          | File object that will be uploaded. Follow [Request File Object Description](#request-file-object-description) section   |
| signers      |  Mandatory   | Array of Object | Array containing signer objects. Follow [Request Signer Object Description](#request-signer-object-description) section |

### Request File Object Description

| Key          | Requirement | Type    | Description                             |
| :---         | :---        | :---    | :---                                    |
| filename     | Mandatory   | String  | Name of the file                        |
| content      | Mandatory   | String  | Base64 encoded file content             |
| callbackUrl  | Optional    | String  | Callback URL to send uuid after signing |

### Request Signer Object Description

| Key        | Requirement | Type    | Description                                                                        |
| :---       | :---        | :---    | :---                                                                               |
| name       | Mandatory   | String  | Signer's name                                                                      |
| surname    | Mandatory   | String  | Signer's surname                                                                   |
| email      | Mandatory   | String  | Signer's email                                                                     |
| successUrl | Optional    | String  | Document upload success redirection URL                                            |
| noEmail    | Optional    | Boolean | If TRUE them email with invitation URL will not be sent to signer (default: false) |

## Response Body Parameter Description

| Key      | Type              | Description                                                                                                                                                                     |
| :---     | :---              | :---                                                                                                                                                                           |
| status   | String            | Status of the request, `ok` if suucess, otherwise `error`                                                                                                                       |
| message  | String            | Status message                                                                                                                                                                 |
| signers  | Array of Objects  | Array containing signer objects that was provided in request along with other infos. Follow [Response Signer Object Description](#response-signer-object-description) section |

### Response Signer Object Description

| Key            | Type    | Description               |
| :---           | :---    | :---                      |
| name           | String  | Signer's name             |
| surname        | String  | Signer's surname          |
| invitationUrl  | String  | URL to invite this signer |

