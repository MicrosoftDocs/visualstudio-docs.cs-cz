---
title: Úlohy nástroje MSBuild specifické pro Visual C++ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks specific to Visual C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 452c3b408ab6471963124e61bc803e99eb6be80d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686910"
---
# <a name="msbuild-tasks-specific-to-visual-c"></a>Úlohy nástroje MSBuild specifické pro Visual C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Úlohy poskytují kód, který se spouští během procesu sestavení. Při instalaci Visual C++ jsou k dispozici následující úkoly kromě těch, které jsou nainstalovány s nástrojem [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Další informace naleznete v tématu [MSBuild (Visual C++) – přehled](https://msdn.microsoft.com/library/dd258f6f-ab51-48d9-b274-f7ba911d05ca).  
  
 Kromě parametrů pro každý úkol má každý úkol také následující parametry.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Condition`|Volitelný `String` parametr.<br /><br /> `Boolean`Výraz, který [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] modul používá k určení, zda bude tento úkol proveden. Informace o podmínkách podporovaných nástrojem najdete [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] v tématu [podmínky](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Volitelný parametr. Může obsahovat jednu z následujících hodnot:<br /><br /> -   **WarnAndContinue** nebo **true**. Pokud se úloha nezdařila, následné úkoly v [cílovém](../msbuild/target-element-msbuild.md) elementu a sestavení se budou spouštět i nadále a všechny chyby z tohoto úkolu jsou považovány za upozornění.<br />-   **ErrorAndContinue**. Pokud se úloha nezdařila, následné úkoly v `Target` elementu a sestavení se budou dále spouštět a všechny chyby z tohoto úkolu jsou považovány za chyby.<br />-   **ErrorAndStop** nebo **false** (výchozí). Pokud se úloha nepovede, zbývající úkoly v `Target` elementu a sestavení se nezpracují a celý `Target` element a sestavení se považují za neúspěšné.<br /><br /> Verze .NET Framework před 4,5 podporovaly pouze `true` `false` hodnoty a.<br /><br /> Další informace najdete v tématu [Postupy: ignorování chyb v úlohách](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[BscMake – úloha](../msbuild/bscmake-task.md)|Zabalí Nástroj pro údržbu informací o procházení Microsoftem (bscmake.exe).|  
|[CL – úloha](../msbuild/cl-task.md)|Zabalí nástroj kompilátoru Visual C++ (cl.exe).|  
|[CPPClean – – úloha](../msbuild/cppclean-task.md)|Odstraní dočasné soubory, které nástroj MSBuild vytvoří při sestavení projektu Visual C++.|  
|[LIB – Úloha](../msbuild/lib-task.md)|Zabalí nástroj Správce bitových knihoven Microsoft 32 (lib.exe).|  
|[Propojit úkol](../msbuild/link-task.md)|Zabalí nástroj Visual C++ Linker (link.exe).|  
|[MIDL – úloha](../msbuild/midl-task.md)|Zabalí nástroj kompilátoru MIDL (Microsoft Interface Definition Language) (midl.exe).|  
|[MT – úloha](../msbuild/mt-task.md)|Zabalí Nástroj manifest společnosti Microsoft (mt.exe).|  
|[RC – úloha](../msbuild/rc-task.md)|Zabalí nástroj Microsoft Windows Resource Compiler (rc.exe).|  
|[Setenv – – úloha](../msbuild/setenv-task.md)|Nastaví nebo odstraní hodnotu zadané proměnné prostředí.|  
|[VCMessage – – úloha](../msbuild/vcmessage-task.md)|Protokoluje zprávy upozornění a chybové zprávy během sestavení.|  
|[XDCMake – úloha](../msbuild/xdcmake-task.md)|Zabalí Nástroj dokumentace XML (xdcmake.exe), který sloučí soubory komentáře dokumentu XML (. xdc) do souboru. XML.|  
|[XSD – úloha](../msbuild/xsd-task.md)|Zabalí Nástroj definice schématu XML (xsd.exe), který generuje soubory schématu nebo třídy ze zdroje.|  
|[Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)|Popisuje prvky systému MSBuild.|  
|[Úlohy](../msbuild/msbuild-tasks.md)|Popisuje úlohy, které jsou jednotky kódu, které mohou být kombinovány pro vytvoření sestavení.|  
|[Zápis úlohy](../msbuild/task-writing.md)|Popisuje, jak vytvořit úlohu.|
