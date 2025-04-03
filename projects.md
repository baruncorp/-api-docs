---
layout: default
title: Projects
---

# Projects

The Projects endpoint allows you to search for projects within the BarunCorp BMS system. You can filter projects by address, property type, and property owner using query parameters.

## Endpoint

```
GET https://api-public.baruncorp.com/prod/projects
```

## Query Parameters

- **propertyFullAddress** (optional)  
  A full or partial address to filter projects by property location.

- **propertyType** (optional)  
  Filter projects by property type. Accepted values: `Residential` or `Commercial`.

- **projectPropertyOwner** (optional)  
  A full or partial name to filter projects by the property owner's name.

## Example Request

```
GET https://api-public.baruncorp.com/prod/projects?propertyFullAddress=Main%20Street&propertyType=Residential&projectPropertyOwner=Smith
```

## Example Response

```json
{
  "totalCount": 115230,
  "pageSize": 20,
  "page": 1,
  "totalPage": 5762,
  "items": [
    {
      "projectId": "0d36f020-c063-4bc3-8f1f-5f2b13a8b23e",
      "organizationId": "9eb764b5-be7c-42f7-84f7-c823c6edf6b8",
      "organizationName": "EMT Solar_",
      "propertyOwnerName": "Christopher Vivarelli",
      "propertyType": "Residential",
      "projectFolderLink": null,
      "projectNumber": null,
      "propertyFullAddress": "1110 Furman Dr, Egg Harbor Township, NJ 08234, USA",
      "createdAt": "2025-04-03T17:30:43.000Z",
      "totalOfJobs": 1,
      "masterLogUpload": false,
      "designOrPEStampPreviouslyDoneOnProjectOutSide": false,
      "mountingType": "Roof Mount"
    },
    {
      "projectId": "1110c1ed-bd2d-4dd6-bc26-b947229bad07",
      "organizationId": "9eb764b5-be7c-42f7-84f7-c823c6edf6b8",
      "organizationName": "EMT Solar_",
      "propertyOwnerName": null,
      "propertyType": "Residential",
      "projectFolderLink": null,
      "projectNumber": null,
      "propertyFullAddress": "608 East Saint Johns Avenue, Villas, New Jersey 08251, United States",
      "createdAt": "2025-04-03T17:24:26.000Z",
      "totalOfJobs": 1,
      "masterLogUpload": false,
      "designOrPEStampPreviouslyDoneOnProjectOutSide": false,
      "mountingType": "Roof Mount"
    },
    {
      "projectId": "4b447d4f-6ba4-465d-9c88-595a9c68e276",
      "organizationId": "e7655b97-ee63-46f0-94ea-f5f468637711",
      "organizationName": "Freedom Forever_",
      "propertyOwnerName": "Barton Arellano",
      "propertyType": "Residential",
      "projectFolderLink": null,
      "projectNumber": "530277",
      "propertyFullAddress": "5418 Murchison Ave SW, Albuquerque, NM 87121, USA",
      "createdAt": "2025-04-03T16:53:07.000Z",
      "totalOfJobs": 1,
      "masterLogUpload": false,
      "designOrPEStampPreviouslyDoneOnProjectOutSide": false,
      "mountingType": "Roof Mount"
    }
    // ... additional projects
  ]
}
```

## Notes

- **Pagination:**  
  The response includes fields like `totalCount`, `pageSize`, `page`, and `totalPage` to help you navigate large datasets.

- **Usage of `projectId`:**  
  The `projectId` returned for each project is crucial when creating a job. Ensure you capture this ID to reference the project in subsequent job submissions.

- **Filtering:**  
  All query parameters are optional. If no parameters are specified, the endpoint returns all projects accessible to your account. Filtering is case-insensitive.

For further questions or support, please reach out to [tylery@baruncorp.com](mailto:tylery@baruncorp.com).