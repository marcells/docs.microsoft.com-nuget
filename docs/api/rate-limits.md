---
title: Rate Limits, NuGet API
description: The NuGet APIs will have enforced rate limits to prevent abuse.
author: cmanu
ms.author: cmanu
manager: skofman
ms.date: 03/20/2018
ms.topic: reference
ms.reviewer:
  - skofman
  - anangaur
  - kraigb
---

# Rate Limits

The NuGet.org API enforces rate limiting to prevent abuse. Requests that exceed the rate limit return the following error: 

  ~~~
    {
      "statusCode": 429,
      "message": "Rate limit is exceeded. Try again in 56 seconds."
    }
  ~~~

The following tables list the rate limits for the NuGet.org API.

## Package search

> [!Note]
> We recommend using NuGet.org's [V3 APIs](https://docs.microsoft.com/nuget/api/search-query-service-resource) for search that are performant and do not have any limit currently. For V1 and V2 search APIs, the followins limits apply:


| API | Limit Type | Limit Value | API usecase |
|:---|:---|:---|:---|
**GET** `/api/v1/Packages` | IP | 1000 / minute | Query NuGet package metadata via v1 OData `Packages` collection |
**GET** `/api/v1/Search()` | IP | 3000 / minute | Search for NuGet packages via v1 Search endpoint | 
**GET** `/api/v2/Packages` | IP | 20000 / minute | Query NuGet package metadata via v2 OData `Packages` collection | 
**GET** `/api/v2/Packages/$count` | IP | 100 / minute | Query NuGet package count via v2 OData `Packages` collection | 

## Package Push and Unlist

| API | Limit Type | Limit Value | API usecase | 
|:---|:---|:---|:--- |
**PUT** `/api/v2/package` | API Key | 100 / minute | Upload a new NuGet package (version) via v2 push endpoint 
**DELETE** `/api/v2/package/{id}/{version}` | API Key | 100 / minute | Unlist a NuGet package (version) via v2 endpoint 
