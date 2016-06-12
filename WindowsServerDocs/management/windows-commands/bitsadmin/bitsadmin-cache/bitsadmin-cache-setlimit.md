---
title: bitsadmin cache and setlimit
ms.custom: na
ms.prod: windows-server-2012
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 46578835-d5ce-423b-be4d-62ddb9e1908d
---
# bitsadmin cache and setlimit
Sets the cache size limit.

## Syntax

```
bitsadmin /Cache /SetLimit Percent
```

## Parameters

|Parameter|Description|
|-------------|---------------|
|Percent|The cache limit defined as a percentage of the total hard disk space..|

## <a name="BKMK_examples"></a>Examples
The following example limits the cache size to 50%.

```
C:\>bitsadmin /Cache /SetLimit 50 
```

## additional references
[Command-Line Syntax Key](../../commandline-syntax-key.md)

