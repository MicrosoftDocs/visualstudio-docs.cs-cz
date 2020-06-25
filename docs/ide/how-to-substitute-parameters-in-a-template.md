---
title: Přidání parametrů názvu do šablon projektů a položek
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 3c8b6e0570567e8eb696fda61fe9db7bbd4a2f1b
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283941"
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
