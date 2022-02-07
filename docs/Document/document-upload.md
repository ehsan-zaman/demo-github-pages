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

## Request Body Parameters

| Key | Description | Requirement | Type |
| :--- | :--- | :--- | :--- |
| access_token | API Access Token | Mandatory | String |
| access | Document access. Possible values: public, private | Mandatory | String |
| file | File object that will be uploaded | Mandatory | Object |
| signers | Array containing signer objects | Mandatory | Array of Object |
