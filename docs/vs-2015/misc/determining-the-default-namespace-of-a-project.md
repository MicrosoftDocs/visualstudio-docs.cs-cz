---
title: Určení výchozího oboru názvů projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- custom tools, computing default namespace
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 1d58c8986922c30192d6300a623a635b24c34ed5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705776"
---
# <a name="determining-the-default-namespace-of-a-project"></a>Určení výchozího oboru názvů projektu
Pro [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , pokud `CustomToolNamespace` je vlastnost nastavena na vstupním souboru, pak hodnota `CustomToolNamespace` se bude hodnotou výchozího parametru oboru názvů předaného <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> metodě. V opačném případě `wszDefaultNamespace` je parametr předaný na `Generate` hodnotu vždy stejný jako kořenový obor názvů. Další informace o oborech názvů najdete v tématu [klíčová slova oboru názvů](https://msdn.microsoft.com/library/091a66eb-b10d-4f54-9102-5ac0d4bdb84b).  
  
 [!INCLUDE[csprcs](../includes/csprcs-md.md)] používá obory názvů založené na složkách. To znamená, že obor názvů se skládá z kořenového oboru názvů a navíc názvy všech složek, které obsahují vlastní nástroj. Každý název složky je převeden na platný identifikátor a tečky oddělují všechny názvy. Například pokud je vstupní soubor FolderA\FolderB\FolderC\MyInput.txt a kořenový obor názvů je CL9, vypočítaný výchozí obor názvů bude **CL9. Složka.. FolderB. FolderC**.  
  
 K výjimce z tohoto pravidla dochází, pokud řetěz hierarchie obsahuje složku webového odkazu. Například pokud:  
  
- FolderC byly složky webového odkazu, obor názvů by **CL9. FolderC**.  
  
- FolderB byly složky webového odkazu, obor názvů by **CL9. FolderB. FolderC**.  
  
  To znamená, že obor názvů používá následující formát:  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## <a name="see-also"></a>Viz také  
 [Implementace generátorů tvořených jedním souborem](../extensibility/internals/implementing-single-file-generators.md)   
 [Registrace generátorů s jedním souborem](../extensibility/internals/registering-single-file-generators.md)   
 [Zveřejnění typů pro vizuální návrháře](../extensibility/internals/exposing-types-to-visual-designers.md)