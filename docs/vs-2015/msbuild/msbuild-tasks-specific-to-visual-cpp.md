---
title: Úlohy nástroje MSBuild specifické pro Visual C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 1da9bdb5c181c9fd935987d629f08af1505f0501
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246145"
---
# <a name="msbuild-tasks-specific-to-visual-c"></a>Úlohy nástroje MSBuild specifické pro Visual C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Úlohy poskytují kód, který se spustí během procesu sestavení. Při instalaci Visual C++ jsou k dispozici, kromě těch, které se instalují s následující úlohy [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Další informace najdete v tématu [přehled nástroje MSBuild (Visual C++)](http://msdn.microsoft.com/library/dd258f6f-ab51-48d9-b274-f7ba911d05ca).  
  
 Kromě parametrů pro každou úlohu Každá úloha má také následující parametry.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Condition`|Volitelné `String` parametru.<br /><br /> A `Boolean` výraz, který [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] modul se používá k určení, zda se tato úloha spustí. Informace o podmínkách, které jsou podporovány [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], naleznete v tématu [podmínky](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Volitelný parametr. Může obsahovat jednu z následujících hodnot:<br /><br /> -   **WarnAndContinue** nebo **true**. Při selhání úkolu, následné úlohy v [cílové](../msbuild/target-element-msbuild.md) elementu a sestavení budou dál spouštět a všechny chyby z úlohy jsou považovány za upozornění<br />-   **ErrorAndContinue**. Při selhání úkolu, následné úlohy v `Target` elementu a sestavení budou dál spouštět a všechny chyby z úlohy jsou považována za chyby.<br />-   **ErrorAndStop** nebo **false** (výchozí). Při selhání úkolu, ve zbývajících úkolech v`Target` elementu a sestavení nejsou provedeny a celé `Target` elementu a sestavení jsou považovány za neúspěšný.<br /><br /> Verze rozhraní .NET Framework před 4.5 podporována pouze `true` a `false` hodnoty.<br /><br /> Další informace najdete v tématu [postupy: ignorování chyb v úlohách](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[BscMake – úloha](../msbuild/bscmake-task.md)|Zabalí nástroj Microsoft procházet informace nástroje pro správu (bscmake.exe).|  
|[CL – úloha](../msbuild/cl-task.md)|Zabalí nástroj kompilátoru Visual C++ (cl.exe).|  
|[CPPClean – úloha](../msbuild/cppclean-task.md)|Odstraní dočasné soubory, které MSBuild vytvoří při vytváření projektu Visual C++.|  
|[LIB – úloha](../msbuild/lib-task.md)|Zabalí nástroj Správce 32bitové Microsoft knihovny (lib.exe).|  
|[Odkaz – úloha](../msbuild/link-task.md)|Zabalí nástroj linker Visual C++ (link.exe).|  
|[MIDL – úloha](../msbuild/midl-task.md)|Zabalí nástroj kompilátoru Microsoft Interface Definition Language (MIDL) (midl.exe).|  
|[MT – úloha](../msbuild/mt-task.md)|Zabalí nástroj Microsoft Manifest (mt.exe).|  
|[RC – úloha](../msbuild/rc-task.md)|Zabalí nástroj Microsoft Windows Resource Compiler (rc.exe).|  
|[SetEnv – úloha](../msbuild/setenv-task.md)|Nastaví nebo vymaže hodnotu proměnné zadané prostředí.|  
|[VCMessage – úloha](../msbuild/vcmessage-task.md)|Protokoly upozornění a chybové zprávy během sestavení.|  
|[XDCMake – úloha](../msbuild/xdcmake-task.md)|Zabalí nástroj dokumentace XML (xdcmake.exe), která sloučí soubory komentáře (.xdc) dokumentu XML do souboru .xml.|  
|[XSD – úloha](../msbuild/xsd-task.md)|Zabalí nástroj definici schématu XML (xsd.exe), který generuje schématu nebo třída soubory ze zdroje.|  
|[Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)|Popisuje elementy systém MSBuild.|  
|[Úlohy](../msbuild/msbuild-tasks.md)|Popisuje úlohy, jako jsou jednotky kódu, které mohou být kombinovány pro vytvoření sestavení.|  
|[Zápis úloh](../msbuild/task-writing.md)|Popisuje, jak vytvořit úlohu.|



