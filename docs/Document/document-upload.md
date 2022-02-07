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

| Key          | Description                                                                                                             | Requirement | Type            |
| :---         | :---                                                                                                                    | :---        | :---            |
| access_token | API Access Token                                                                                                        | Mandatory   | String          |
| access       | Document access. Possible values: public, private                                                                       | Mandatory   | String          |
| file         | File object that will be uploaded. Follow [Request File Object Description](#request-file-object-description) section   | Mandatory   | Object          |
| signers      | Array containing signer objects. Follow [Request Signer Object Description](#request-signer-object-description) section | Mandatory   | Array of Object |

### Request File Object Description

| Key          | Description                             | Requirement | Type    |
| :---         | :---                                    | :---        | :---    |
| filename     | Name of the file                        | Mandatory   | String  |
| content      | Base64 encoded file content             | Mandatory   | String  |
| callbackUrl  | Callback URL to send uuid after signing | Optional    | String  |

### Request Signer Object Description

| Key        | Description                                                                         | Requirement | Type    |
| :---       | :---                                                                                | :---        | :---    |
| name       | Signer's name                                                                       | Mandatory   | String  |
| surname    | Signer's surname                                                                    | Mandatory   | String  |
| email      | Signer's email                                                                      | Mandatory   | String  |
| successUrl | Document upload success redirection URL                                             | Optional    | String  |
| noEmail    | If TRUE them email with invitation URL will not be sent to signer (default: false)  | Optional    | Boolean |
