---
title: "Role-based access controls - Basic use cases"
slug: rbac-use-cases-basic
---


The following use cases illustrate the flexibility of CloudMC roles with real-world examples.  Unless otherwise indicated, the examples assume the user account has a primary role of *Guest*, no additional roles,  *Viewer* access on one environment in the organization, and that the account is created in the organization intended to be accessed.  These are examples only, individual needs will vary.

The diagram below depicts three hypothetical organizations with environments and a sub-organization.  Note that Organization A has two tags, **billable** and **managed**, and Sub-organization C has one tag, **billable**.  Organization D is an approved trial, automatically tagged with **trial**.

![use cases diagram](/assets/rbac-use-cases-trial-en.png)

| Scenario | Suggested role name | Role configuration | Notes from example |
| --- | --- | --- | --- |
| Access to environment, list resources | Not applicable | Primary role *Guest*, *Viewer* access on the assigned environments in the organization | Applied to a user in Organization B and a member of environment2, this would grant read-only access to only environment2 |
| Approve, deny, and other trial-related functions | Trials Administrator | Additional custom role with the *Trials: Manage* permission.  Role must use *All organizations with tag: trial* for scope | Applied to a user in any organization, the user can manage the trial options for Organization D, but cannot manage any organizations |
| Create and delete users only | User Manager | Additional custom role with the *Users: Manage* permission, scoped for the desired organizations | Applied to a user in Organization B with scope **Only the sub-organizations of a specific organization** and specifying Organization B, this access would be granted only for Sub-organization C |
| Create, edit, and delete knowledge base articles | Content Manager | Additional custom role with the *Content: Manage* permission.  Role must use *All organizations* for scope | Applied to a user in any organization, the user can manage the knowledge base articles, shared by all organizations |
| Select logos and colour schemes | Branding Manager | Additional custom role with the permissions *Branding: Manage*, and *System state:View*. Role must use *All organizations* for scope | Applied to a user in any organization, the user can manage the system branding for CloudMC |
