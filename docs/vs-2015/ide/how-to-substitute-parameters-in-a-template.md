---
title: 'Postupy: nahrazení parametrů v šabloně | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- template parameters, substituting
- Visual Studio templates, using parameters
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fe49c928ca3de318410eba56afeae6f4329efed3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670665"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Postupy: Nahrazení parametrů v šabloně
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete nahradit parametry šablony, jako jsou názvy tříd a obory názvů, když je vytvořen soubor založený na šabloně. Úplný seznam parametrů šablony najdete v tématu [parametry šablony](../ide/template-parameters.md).

## <a name="procedure"></a>Postup
 Můžete nahradit parametry v souborech šablony vždy, když je vytvořen projekt založený na této šabloně. Tento postup vysvětluje, jak vytvořit šablonu, která nahradí název oboru názvů názvem bezpečného projektu při vytvoření nového projektu pomocí šablony.

#### <a name="to-use-a-parameter-to-replace-namespace-name-with-the-project-name"></a>Chcete-li použít parametr k nahrazení názvu oboru názvů názvem projektu

1. Vložte parametr do jednoho nebo více souborů kódu v šabloně. Příklad:

    ```
    namespace $safeprojectname$
    ```

    > [!NOTE]
    > Parametry šablony jsou zapsané ve formátu $*Parameter*$.

2. V souboru. vstemplate pro šablonu vyhledejte `ProjectItem` prvek, který obsahuje tento soubor.

3. Nastavte `ReplaceParameters` atribut pro `true` `ProjectItem` element. Příklad:

    ```
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Viz také
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md) [parametrů šablony](../ide/template-parameters.md) sady [Visual Studio Referenční schéma](../extensibility/visual-studio-template-schema-reference.md) [prvku ProjectItem (šablony položek sady Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
