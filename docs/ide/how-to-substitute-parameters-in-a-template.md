---
title: Přidání parametrů názvu do šablon projektů a položek
description: Naučte se, jak upravit parametry šablony a nahradit identifikátory jako názvy tříd a obory názvů.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: ba830035f441421ca0eb83404b37319d9a9e2ca3
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/24/2020
ms.locfileid: "95596856"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Postupy: nahrazení parametrů v šabloně

Parametry šablony umožňují nahradit identifikátory, jako jsou názvy tříd a obory názvů, při vytvoření souboru ze šablony. Můžete přidat parametry šablony do existujících šablon nebo vytvořit vlastní šablony s parametry šablony.

Parametry šablony jsou zapsané ve formátu $*Parameter*$. Úplný seznam parametrů šablony najdete v tématu [parametry šablony](../ide/template-parameters.md).

V následující části se dozvíte, jak upravit šablonu, aby nahradila název oboru názvů názvem bezpečného projektu.

## <a name="example---namespace-name"></a>Příklad – název oboru názvů

1. Vložte parametr do jednoho nebo více souborů kódu v šabloně. Například:

    ```csharp
    namespace $safeprojectname$
    ```

1. V souboru *vstemplate* pro šablonu vyhledejte `ProjectItem` prvek, který obsahuje tento soubor.

1. Nastavte `ReplaceParameters` atribut `true` pro `ProjectItem` element:

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Viz také

- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Parametry šablony](../ide/template-parameters.md)
- [Referenční dokumentace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [ProjectItem – element (šablony položek sady Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
