---
title: XSD – úloha | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: 0c9dcc0d09887cacca7e6cdaa2e4f2b719c6451c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "67826248"
---
# <a name="xsd-task"></a>XSD – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zabalí Nástroj definice schématu XML (xsd.exe), který generuje soubory schématu nebo třídy ze zdroje.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry úlohy **XSD** .  
  
- **AdditionalOptions**  
  
     Volitelný **řetězcový** parametr.  
  
     Seznam možností, jak je uvedeno na příkazovém řádku. Například "*/option1/option2/Option #*". Pomocí tohoto parametru můžete zadat možnosti, které nejsou reprezentované žádným jiným parametrem úlohy **XSD** .  
  
- **GenerateFromSchema**  
  
  Volitelný **řetězcový** parametr.  

  Určuje typy, které jsou generovány ze zadaného schématu.  

  Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti XSD.  

  - **třídy**  -  **/Classes**  

  - **datová sada**  -  **/DataSet**  
  
- **Jazyk**  
  
     Volitelný **řetězcový** parametr.  
  
     Určuje programovací jazyk, který má být použit pro vygenerovaný kód.  
  
     Vyberte z **cs** (C#, což je výchozí), **VB** (Visual Basic) nebo **js** (JScript). Můžete také zadat plně kvalifikovaný název pro třídu, která implementuje `System.CodeDom.Compiler.CodeDomProvider Class`.  
  
- **Obor názvů**  
  
     Volitelný **řetězcový** parametr.  
  
     Určuje runtime obor názvů pro generovaný typy.  
  
- **zdroje**  
  
     Požadovaný parametr `ITaskItem[]`.  
  
     Definuje pole položek zdrojového souboru MSBuild, které mohou být spotřebovány a generovány úlohami.  
  
- **SuppressStartupBanner**  
  
     Volitelný **logický** parametr.  
  
     Pokud `true` aplikace zabrání zobrazení zprávy o autorských právech a číslech verze při spuštění úlohy.  
  
- **TrackerLogDirectory**  
  
     Volitelný **řetězcový** parametr.  
  
     Určuje adresář pro protokol sledování.  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
