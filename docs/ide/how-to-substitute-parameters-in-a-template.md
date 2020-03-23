---
title: Přidání parametrů názvu do šablon projektů a položek
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591408"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Postup: Nahrazení parametrů v šabloně

Parametry šablony umožňují nahradit identifikátory, jako jsou názvy tříd a obory názvů při vytvoření souboru ze šablony. Do existujících šablon můžete přidat parametry šablony nebo vytvořit vlastní šablony s parametry šablony.

Parametry šablony jsou zapsány ve formátu $*parametr*$. Úplný seznam parametrů šablony naleznete v tématu [Parametry šablony](../ide/template-parameters.md).

V následující části se zobrazí způsob, jak upravit šablonu tak, aby nahradila název oboru názvů názvem "bezpečný název projektu".

## <a name="example---namespace-name"></a>Příklad - název oboru názvů

1. Vložte parametr do jednoho nebo více souborů kódu v šabloně. Například:

    ```csharp
    namespace $safeprojectname$
    ```

1. V souboru *vstemplate* pro šablonu vyhledejte `ProjectItem` prvek, který obsahuje tento soubor.

1. Nastavte `ReplaceParameters` atribut `true` pro `ProjectItem` prvek:

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Viz také

- [Vytvoření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Parametry šablony](../ide/template-parameters.md)
- [Odkaz na schéma šablony sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Element ProjectItem (šablony položek sady Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
