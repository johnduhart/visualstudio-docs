---
title: "Extract method - Refactoring (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
    - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.devlang: VB
ms.assetid: 8ad16c15-432b-4b8c-86fd-5f31ad652d24
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
f1_keywords:
	- "vs.csharp.refactoring.extractmethod"
dev_langs:
    - "VB"
translation.priority.ht: 
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

# Extract a method in Visual Basic
**What:** Lets you turn a fragment of code into its own method.

**When:** You have a fragment of existing code in some method that needs to be called from another method.  

**Why:** You could copy/paste that code, but that would lead to duplication.  A better solution is to refactor that fragment into its own method which can be called freely by any other method.

**How:**

1. Highlight the code to be extracted:

   ![Highlighted code](media/extractmethod_highlight.png)

1. Next, do one of the following:
   * **Keyboard**
     * Press **Ctrl+R**, then **Ctrl+M**.  (Note that your keyboard shortcut may be different based on which profile you've selected.)
     * Press **Ctrl+.** to trigger the **Quick Actions and Refactorings** menu and select **Extract Method** from the Preview window popup.
   * **Mouse**
     * Select **Edit > Refactor > Extract Method**.
     * Right-click the code and select **Refactor > Extract > Extract Method**.
     * Right-click the code, select the **Quick Actions and Refactorings** menu and select **Extract Method** from the Preview window popup.

   The method will be immediately created.  From here, you can now rename the method simply by typing the new name.

   > [!TIP]
   > You can also update comments and other strings to use this new name, as well as [preview changes](../../ide/preview-changes.md) before saving, using the checkboxes in the **Rename** box which appears at the top right of your IDE.

   ![Rename method](media/extractmethod_rename.png)

1. When you're happy with the change, click the **Apply** button or press **Enter** and the changes will be committed.

## See Also  
[Refactoring (Visual Basic)](../refactoring-vb.md)  
[Preview Changes](../../ide/preview-changes.md)