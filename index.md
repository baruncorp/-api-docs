---
layout: default
title: BarunCorp Public API Documentation
---

# 👋 Welcome to the BarunCorp Public API

The BarunCorp Public API provides direct access to our internal **BMS system**, allowing you to:

- **Submit new projects and jobs** into our system  
- **View existing jobs and projects**  
- **Retrieve invoice data** (read-only)

This API streamlines data intake and gives you real-time insights into job progress and billing.

---

## Navigation

- [Authentication](authentication.md) — Learn how to generate your access token.
- [Projects](projects.md) — Submit projects, search projects, view projects.
- [Jobs](jobs.html) — Submit jobs, and view job details.
- [Invoices](invoices.html) — View invoice data and associated information.

---

## Overview

Use this API to integrate your systems with our BMS. Whether you're automating job submissions or tracking invoices, our API ensures you stay connected with BarunCorp’s internal operations.

---

## 🔁 Workflow: Creating a Job

To create a job using the API, follow this typical workflow:

1. **Check if a project exists for the given address**
   - Use the [Projects endpoint](projects.md) to query by address or project attributes.
   - If a project exists, retrieve its `project_id` and `organization_id`.

2. **Create a new project (if needed)**
   - If no existing project matches, use the Projects endpoint to submit a new one.
   - Save the returned `project_id` from the response.

3. **Create the job**
   - Use the [Jobs endpoint](jobs.html) and include the `project_id` in your job submission payload.

This workflow ensures all jobs are correctly associated with their corresponding projects in the BMS system.

For support, please email [tylery@baruncorp.com](mailto:tylery@baruncorp.com).