---
title: "Project Modeling | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "automation [Visual Studio SDK], implementing project objects"
  - "project models, automation"
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
translation.priority.mt: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---
# Project Modeling
The next step in providing automation for your project is to implement the standard project objects: the <xref:EnvDTE.Projects> and `ProjectItems` collections; the `Project` and <xref:EnvDTE.ProjectItem> objects; and the remaining objects unique to your implementation. These standard objects are defined in Dteinternal.h file. An implementation of the standard objects is provided in the BscPrj sample. You can use these classes as models to create your own standard project objects that stand side-by-side with project objects from other project types.  
  
 An automation consumer presumes to be able to call <xref:EnvDTE.Solution>("`<UniqueProjName>")` and <xref:EnvDTE.ProjectItems> (`n`) where n is an index number for obtaining a specific project in the solution. Making this automation call causes the environment to call <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> on the appropriate project hierarchy, passing VSITEMID_ROOT as the ItemID parameter and VSHPROPID_ExtObject as VSHPROPID parameter. `IVsHierarchy::GetProperty` returns an `IDispatch` pointer to the automation object providing the core `Project` interface, which you have implemented.  
  
 The following is the syntax of `IVsHierarchy::GetProperty`.  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT` `*pvar`  
  
 `);`  
  
 Projects accommodate nesting and use collections to create groups of project items. The hierarchy looks like this.  
  
```  
Projects  
  |– Project  
      |– ProjectItems (a collection of ProjectItem)  
          |– ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 Nesting means that a <xref:EnvDTE.ProjectItem> object can be <xref:EnvDTE.ProjectItems> collection at the same time because a `ProjectItems` collection can contain the nested objects. The Basic Project sample does not demonstrate this nesting. By implementing the `Project` object, you participate in the tree-like structure that characterizes the design of the overall automation model.  
  
 The project automation follows the path in the following diagram.  
  
 ![Visual Studio Project Objects](../../extensibility/internals/media/projectobjects.gif "ProjectObjects")  
Project automation  
  
 If you do not implement a `Project` object, the environment will still return a generic `Project` object that contains only the name of the project.  
  
## See Also  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>