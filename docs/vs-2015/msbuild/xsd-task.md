---
title: XSD – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.task.xsd
- VC.Project.VCXMLDataGeneratorTool.Namespace
- VC.Project.VCXMLDataGeneratorTool.GenerateFromSchema
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XSD task (MSBuild (Visual C++))
- MSBuild (Visual C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd1aed6537d4fb49bafa34ce09dcb191c9475357
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49182634"
---
# <a name="xsd-task"></a>XSD – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Zabalí nástroj definici schématu XML (xsd.exe), který generuje schématu nebo třída soubory ze zdroje.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry **XSD** úloh.  
  
-   **AdditionalOptions**  
  
     Volitelné **řetězec** parametru.  
  
     Seznam možností, jak je uvedeno na příkazovém řádku. Například "*/option1 /option2 /option#*". Tento parametr použijte k určení možností, které nejsou reprezentovány jakýkoli jiný **XSD** parametr úlohy.  
  
-   **GenerateFromSchema**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje typy, které se generují z určené schéma.  
  
     Zadejte jednu z následujících hodnot, z nichž každý odpovídá možnost XSD.  
  
    -   **třídy** -   **/třídy**  
  
    -   **dataset** - **/dataset**  
  
-   **Jazyk**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje programovací jazyk pro použití generovaného kódu.  
  
     Vyberte si z **CS** (C#, což je výchozí hodnota), **VB** (Visual Basic), nebo **JS** (JScript). Můžete také zadat plně kvalifikovaný název pro třídu, která implementuje `System.CodeDom.Compiler.CodeDomProvider Class`.  
  
-   **Namespace**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje runtime obor názvů pro generovaný typy.  
  
-   **Zdroje**  
  
     Vyžaduje `ITaskItem[]` parametru.  
  
     Definuje pole objektů položky nástroje MSBuild zdrojových souborů, které lze používat a, protože ho vygeneroval úlohy.  
  
-   **SuppressStartupBanner**  
  
     Volitelné **logická** parametru.  
  
     Pokud `true`, zabraňuje zobrazování čísel zprávu o autorských právech a verze při spuštění úlohy.  
  
-   **TrackerLogDirectory**  
  
     Volitelné **řetězec** parametru.  
  
     Určuje adresář protokolu sledovacího modulu.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)



