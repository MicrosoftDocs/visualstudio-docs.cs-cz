---
title: Přidání názvu parametrů do šablony projektů a položek
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 9ddfe065d30b958e52e22f30f946d01d626fcf0e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591408"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Postupy: nahrazení parametrů v šabloně

Parametry šablony umožňují nahradit identifikátory, jako jsou názvy tříd a obory názvů, když se vytvoří soubor ze šablony. Můžete přidat parametry šablony do stávající šablony, nebo vytvořit vlastní šablony s parametry šablony.

Parametry šablony jsou napsané ve formátu $*parametr*$. Úplný seznam parametrů šablony, najdete v části [parametry šablony](../ide/template-parameters.md).

Následující části se dozvíte, jak upravit šablonu, která nahradit název oboru názvů s názvem"bezpečné projektu".

## <a name="example---namespace-name"></a>Příklad – název oboru názvů

1. Vložte parametr v jednom nebo více souborů s kódem v šabloně. Příklad:

    ```csharp
    namespace $safeprojectname$
    ```

1. V *vstemplate* soubor šablony, vyhledejte `ProjectItem` element, který obsahuje tento soubor.

1. Nastavte `ReplaceParameters` atribut `true` pro `ProjectItem` element:

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Viz také:

- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Parametry šablony](../ide/template-parameters.md)
- [Visual Studio odkaz na schéma šablon](../extensibility/visual-studio-template-schema-reference.md)
- [ProjectItem – element (šablony sady Visual Studio položky)](../extensibility/projectitem-element-visual-studio-item-templates.md)
