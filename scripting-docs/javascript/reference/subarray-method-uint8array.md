---
title: "subarray Method (Uint8Array) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 07724c80-5fdf-4745-a750-214630100439
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# subarray Method (Uint8Array)
Gets a new Uint8Array view of the [ArrayBuffer Object](../../javascript/reference/arraybuffer-object.md) store for this array, specifying the first and last members of the subarray.  
  
## Syntax  
  
```JavaScript  
var newUint8Array = uint8Array.subarray(begin, end);  
```  
  
## Parameters  
 `newUint8Array`  
 The subarray returned by this method.  
  
 `begin`  
 The index of the beginning of the array.  
  
 `end`  
 The index of the end of the array. This is non-inclusive.  
  
## Remarks  
 If either `begin` or `end` is negative, it refers to an index from the end of the array, as opposed to from the beginning. If `end` is unspecified, the subarray contains all elements from `begin` to the end of the typed array. The range specified by the `begin` and `end` values is clamped to the valid index range for the current array. If the computed length of the new typed array would be negative, it is clamped to zero. The returned array is of the same type as the array on which this method is invoked.  
  
## Example  
 The following example shows how to get a subarray two elements long, starting with the first element of the array.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var intArr = new Uint8Array(buffer.byteLength);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## Requirements  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]