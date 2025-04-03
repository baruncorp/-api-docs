---
layout: default
title: Projects
---

# Projects

The Projects endpoint allows you to search for and create projects within the BarunCorp BMS system.

---

## GET /projects s 

```
GET https://api-public.baruncorp.com/prod/projects
```

### Query Parameters

- **propertyFullAddress** (optional)  
  A full or partial address to filter projects by property location.

- **propertyType** (optional)  
  Filter projects by property type. Accepted values: `Residential` or `Commercial`.

- **projectPropertyOwner** (optional)  
  A full or partial name to filter projects by the property owner's name.

### Example Request

```
GET https://api-public.baruncorp.com/prod/projects?propertyFullAddress=Main%20Street&propertyType=Residential&projectPropertyOwner=Smith
```

### Example Response

```json
{
  "totalCount": 2,
  "pageSize": 20,
  "page": 1,
  "totalPage": 1,
  "items": [
    {
      "projectId": "123e4567-e89b-12d3-a456-426614174000",
      "organizationId": "org-001",
      "organizationName": "Sample Organization",
      "propertyOwnerName": "John Doe",
      "propertyType": "Residential",
      "projectFolderLink": null,
      "projectNumber": "PRJ-001",
      "propertyFullAddress": "123 Main St, Anytown, USA",
      "createdAt": "2025-01-01T12:00:00.000Z",
      "totalOfJobs": 2,
      "masterLogUpload": false,
      "designOrPEStampPreviouslyDoneOnProjectOutSide": false,
      "mountingType": "Ground Mount"
    },
    {
      "projectId": "223e4567-e89b-12d3-a456-426614174001",
      "organizationId": "org-002",
      "organizationName": "Another Org",
      "propertyOwnerName": "Jane Smith",
      "propertyType": "Commercial",
      "projectFolderLink": null,
      "projectNumber": "PRJ-002",
      "propertyFullAddress": "456 Elm St, Othertown, USA",
      "createdAt": "2025-02-15T08:30:00.000Z",
      "totalOfJobs": 1,
      "masterLogUpload": false,
      "designOrPEStampPreviouslyDoneOnProjectOutSide": true,
      "mountingType": "Roof Mount"
    }
  ]
}
```

---

## POST /projects

```
POST https://api-public.baruncorp.com/prod/projects
```

### Request Body

```json
{
  "clientOrganizationId": "d3c11b1a-4759-4a26-9f34-b6c2fd3ed83d",
  "projectPropertyOwner": "TEST",
  "projectNumber": "12345",
  "projectPropertyType": "Commercial",
  "projectPropertyAddress": {
    "street1": "East Main Street",
    "street2": "",
    "city": "Coffeen",
    "state": "Illinois",
    "postalCode": "62017",
    "country": "United States",
    "fullAddress": "4234324432 East Main Street, Coffeen, Illinois 62017, United States",
    "coordinates": [-89.381263, 39.085004]
  }
}
```

### Successful Response

```json
{
  "id": "d373d38e-a554-43bc-ab26-71c8a0067a35"
}
```

### Conflict Response (Existing Address)

```json
{
  "errorCode": ["30002"],
  "message": "Project Property Full Address is Already Existed. Existing project ID: d373d38e-a554-43bc-ab26-71c8a0067a35",
  "statusCode": 409,
  "timestamp": "2025-04-03T19:21:42.040Z",
  "path": "/projects"
}
```

---

## Notes

### Pagination  
The GET response includes fields like `totalCount`, `pageSize`, `page`, and `totalPage` to help you navigate large datasets.

### projectId  
The `projectId` is required when creating a job. Capture it from either a new project creation or query results.

### organizationId  
This is also required when submitting a job tied to the project’s organization.

### Filtering  
All query parameters are optional. If none are specified, the GET endpoint returns all projects accessible to your account. Filtering is case-insensitive.

For further support, contact [tylery@baruncorp.com](mailto:tylery@baruncorp.com).