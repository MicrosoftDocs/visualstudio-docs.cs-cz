---
title: Přidání parametrů názvu do šablon projektů a položek
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 09d86c52fcd9ddce3c986e0bfa6c9c96f746c663
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656568"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Postupy: nahrazení parametrů v šabloně

Parametry šablony umožňují nahradit identifikátory, jako jsou názvy tříd a obory názvů, při vytvoření souboru ze šablony. Můžete přidat parametry šablony do existujících šablon nebo vytvořit vlastní šablony s parametry šablony.

Parametry šablony jsou zapsané ve formátu $*Parameter*$. Úplný seznam parametrů šablony najdete v tématu [parametry šablony](../ide/template-parameters.md).

V následující části se dozvíte, jak upravit šablonu, aby nahradila název oboru názvů názvem bezpečného projektu.

## <a name="example---namespace-name"></a>Příklad – název oboru názvů

1. Vložte parametr do jednoho nebo více souborů kódu v šabloně. Příklad:

    ```csharp
    namespace $safeprojectname$
    ```

1. V souboru *vstemplate* pro šablonu vyhledejte prvek `ProjectItem`, který obsahuje tento soubor.

1. Nastavte atribut `ReplaceParameters` pro `true` elementu `ProjectItem`:

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Viz také:

- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Parametry šablony](../ide/template-parameters.md)
- [Referenční dokumentace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [ProjectItem – element (šablony položek sady Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)