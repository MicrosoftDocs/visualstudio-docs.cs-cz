---
title: 'Postupy: nahrazení parametrů v šabloně | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- template parameters, substituting
- Visual Studio templates, using parameters
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bab1d1fd7cd08813dadefbcbec27dbd84bd7b66b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279737"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Postupy: Nahrazení parametrů v šabloně
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete nahradit parametry šablony, jako jsou názvy tříd a obory názvů, když soubor založený na šabloně je vytvořen. Úplný seznam parametrů šablony, najdete v části [parametry šablony](../ide/template-parameters.md).  
  
## <a name="procedure"></a>Postup  
 Pokaždé, když se vytvoří projekt na základě této šablony můžete nahradit parametry v souboru šablony. Tento postup vysvětluje, jak vytvořit šablonu, která se nahradí názvem oboru názvů bezpečný název projektu při vytvoření nového projektu pomocí šablony.  
  
#### <a name="to-use-a-parameter-to-replace-namespace-name-with-the-project-name"></a>Pomocí parametru nahradit název oboru názvů s názvem projektu  
  
1.  Vložte parametr v jednom nebo více souborů s kódem v šabloně. Příklad:  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
    > [!NOTE]
    >  Parametry šablony jsou napsané ve formátu $*parametr*$.  
  
2.  V souboru .vstemplate šablony vyhledejte `ProjectItem` element, který obsahuje tento soubor.  
  
3.  Nastavte `ReplaceParameters` atribut `true` pro `ProjectItem` elementu. Příklad:  
  
    ```  
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)   
 [Parametry šablony](../ide/template-parameters.md)   
 [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [ProjectItem – element (šablony sady Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)



