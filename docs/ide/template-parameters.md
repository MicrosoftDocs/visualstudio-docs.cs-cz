---
title: Parametry šablony projektu a položky
ms.date: 01/02/2018
ms.topic: reference
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 445a4fa7847ea5c9a5cb64da09cf54c763e86d16
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647392"
---
# <a name="template-parameters"></a>Parametry šablony

Můžete nahradit hodnoty v šabloně při vytvoření instance šablony. Chcete-li nastavit tuto funkci, použijte *parametry šablony*. Parametry šablony lze použít k nahrazení hodnot, jako jsou názvy tříd a obory názvů v šabloně. Průvodce šablonou, který běží na pozadí, když uživatel přidá novou položku nebo projekt nahradí tyto parametry.

## <a name="declare-and-enable-template-parameters"></a>Deklarace a povolení parametrů šablony

Parametry šablony jsou deklarovány ve formátu $*Parameter*$. Příklad:

- $safeprojectname $

- $guid $1

- $guid $5

### <a name="enable-parameter-substitution-in-templates"></a>Povolit substituci parametrů v šablonách

1. V souboru *. vstemplate* šablony vyhledejte prvek `ProjectItem`, který odpovídá položce, pro kterou chcete povolit nahrazení parametru.

1. Nastavte atribut `ReplaceParameters` `ProjectItem` elementu na `true`.

1. V souboru kódu pro položku projektu zadejte parametry tam, kde je to vhodné. Například následující parametr určuje, že název bezpečného projektu se používá pro obor názvů v souboru:

    ```csharp
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>Rezervované parametry šablony

Následující tabulka uvádí seznam rezervovaných parametrů šablony, které mohou být použity libovolnou šablonou:

|Parametr|Popis|
|---------------|-----------------|
|ClrVersion|Aktuální verze modulu CLR (Common Language Runtime).|
|ext_*|Přidejte předponu `ext_` do libovolného parametru, abyste odkazovali na proměnné nadřazené šablony. Například `ext_safeprojectname`.|
|GUID [1-10]|Identifikátor GUID, který slouží k nahrazení identifikátoru GUID projektu v souboru projektu. Můžete zadat až 10 jedinečných identifikátorů GUID (například `guid1`).|
|ItemName|Název souboru, ve kterém se parametr používá|
|názevpočítače|Aktuální název počítače (například Computer01).|
|názevprojektu|Jméno, které uživatel zadal při vytvoření projektu.|
|registeredorganization|Hodnota klíče registru z HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization.|
|RootNamespace|Kořenový obor názvů aktuálního projektu Tento parametr platí pouze pro šablony položek.|
|safeitemname|Stejné jako `itemname`, ale všechny nezabezpečené znaky a mezery nahrazují znaky podtržítka.|
|safeitemrootname|Stejné jako `safeitemname`.|
|safeprojectname|Název zadaný uživatelem při vytvoření projektu, ale všechny nezabezpečené znaky a mezery byly odebrány.|
|čas|Aktuální čas ve formátu DD/MM/RRRR 00:00:00.|
|specifiedSolutionName|Název řešení. Pokud je zaškrtnuto políčko „vytvořit adresář řešení“, `specifiedSolutionName` obsahuje název řešení. Pokud není zaškrtnuto políčko „vytvořit adresář řešení“, `specifiedSolutionName` je prázdné.|
|UserDomain|Aktuální doména uživatele.|
|jmen|Aktuální uživatelské jméno.|
|webnamespace|Název aktuálního webu Tento parametr se používá v šabloně webového formuláře k zaručení jedinečných názvů tříd. Pokud se web nachází v kořenovém adresáři webového serveru, tento parametr šablony se přeloží do kořenového adresáře webového serveru.|
|jednolet|Aktuální rok ve formátu YYYY.|

> [!NOTE]
> Parametry šablony rozlišují velká a malá písmena.

## <a name="custom-template-parameters"></a>Parametry vlastní šablony

Kromě výchozích parametrů vyhrazené šablony, které se používají při nahrazování parametrů, můžete zadat vlastní parametry a hodnoty šablon. Další informace naleznete v tématu [CustomParameters – element (šablony sady Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md).

## <a name="example-use-the-project-name-for-a-file-name"></a>Příklad: použití názvu projektu pro název souboru

Můžete zadat názvy souborů proměnných pro položky projektu pomocí parametru v atributu `TargetFileName`.

Následující příklad určuje, že název spustitelného souboru používá název projektu určený `$projectname$`.

```xml
<TemplateContent>
    <ProjectItem
        ReplaceParameters="true"
        TargetFileName="$projectname$.exe">
            File1.exe
    </ProjectItem>
      ...
</TemplateContent>
```

## <a name="example-use-the-safe-project-name-for-the-namespace-name"></a>Příklad: použijte název bezpečného projektu pro název oboru názvů

Chcete-li použít název bezpečného projektu pro obor názvů C# v souboru třídy, použijte následující syntaxi:

```csharp
namespace $safeprojectname$
{
    public class Class1
    {
        public Class1()
        { }
    }
}
```

V souboru *. vstemplate* pro šablonu projektu zahrňte atribut `ReplaceParameters="true"`, když odkazujete na soubor:

```xml
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Viz také:

- [Postupy: nahrazení parametrů v šabloně](how-to-substitute-parameters-in-a-template.md)
- [Přizpůsobení šablon](../ide/customizing-project-and-item-templates.md)
- [Postupy: vytváření šablon projektů](../ide/how-to-create-project-templates.md)
- [Odkaz na schéma šablony](../extensibility/visual-studio-template-schema-reference.md)
