---
title: Parametry šablony projektů a položek
ms.date: 01/02/2018
ms.topic: reference
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 7076e8f5718e44cc382eb0768e6456dbd6ee5664
ms.sourcegitcommit: 1efb6b219ade7c35068b79fbdc573a8771ac608d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78169362"
---
# <a name="template-parameters"></a>Parametry šablony

Při vytváření instance šablony, můžete v šabloně nahraďte hodnoty. Chcete-li nastavit tuto funkci, použijte *parametry šablony*. Parametry šablony lze použít k nahrazení hodnoty, jako jsou názvy tříd a obory názvů v šabloně. Průvodce šablonou, která běží na pozadí, když uživatel přidá nová položka nebo projektu nahradí tyto parametry.

## <a name="declare-and-enable-template-parameters"></a>Deklarace a povolení parametrů šablony

Parametry šablony jsou deklarovány ve formátu $*Parameter*$. Příklad:

- $safeprojectname$

- $guid1$

- $guid5$

### <a name="enable-parameter-substitution-in-templates"></a>Povolit substituci parametrů v šablonách

1. V souboru *. vstemplate* šablony vyhledejte prvek `ProjectItem`, který odpovídá položce, pro kterou chcete povolit nahrazení parametru.

1. Nastavte atribut `ReplaceParameters` `ProjectItem` elementu na `true`.

1. V souboru kódu pro položku projektu zahrnují parametry, kde je to vhodné. Například následující parametr určuje, že se používá bezpečný název projektu pro obor názvů v souboru:

    ```csharp
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>Vyhrazené parametry šablon

Následující tabulka uvádí seznam rezervovaných parametrů šablony, které mohou být použity libovolnou šablonou:

|Parametr|Popis|
|---------------|-----------------|
|clrversion|Aktuální verze modulu common language runtime (CLR).|
|ext_*|Přidejte předponu `ext_` do libovolného parametru, abyste odkazovali na proměnné nadřazené šablony. například `ext_safeprojectname`.|
|identifikátor GUID [1-10]|GUID, který se používá k nahrazení identifikátoru GUID projektu v souboru projektu. Můžete zadat až 10 jedinečných identifikátorů GUID (například `guid1`).|
|Název položky|Název souboru, ve kterém se parametr používá|
|MachineName|Aktuální název počítače (například Computer01).|
|název projektu|Jméno, které uživatel zadal při vytvoření projektu.|
|RegisteredOrganization|Hodnotu klíče registru z HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization.|
|RootNamespace|Kořenový obor názvů aktuálního projektu. Tento parametr platí pouze pro šablony položek.|
|safeitemname|Stejné jako `itemname`, ale všechny nezabezpečené znaky a mezery nahrazují znaky podtržítka.|
|safeitemrootname|Stejné jako `safeitemname`.|
|safeprojectname|Název zadaný uživatelem při vytvoření projektu, ale všechny nezabezpečené znaky a mezery byly odebrány.|
|time|Aktuální čas ve formátu DD/MM/RRRR 00:00:00.|
|specifiedsolutionname|Název řešení. Pokud je zaškrtnuto políčko „vytvořit adresář řešení“, `specifiedsolutionname` obsahuje název řešení. Pokud není zaškrtnuto políčko „vytvořit adresář řešení“, `specifiedsolutionname` je prázdné.|
|USERDOMAIN|Aktuální uživatel domény.|
|uživatelské jméno|Aktuální uživatelské jméno.|
|webnamespace|Název aktuální webové stránky. Tento parametr se používá v šabloně webového formuláře zajistit jedinečné názvy tříd. Pokud webová stránka se v kořenovém adresáři webového serveru, tento parametr šablony přeloží do kořenového adresáře na webovém serveru.|
|rok|Aktuální rok ve formátu RRRR.|

> [!NOTE]
> Parametry šablony jsou malá a velká písmena.

## <a name="custom-template-parameters"></a>Parametry vlastní šablony

Můžete určit vlastní parametry a hodnoty šablony, kromě vyhrazených výchozích parametrů šablony, které se používají při nahrazení parametru. Další informace naleznete v tématu [CustomParameters – element (šablony sady Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md).

## <a name="example-use-the-project-name-for-a-file-name"></a>Příklad: Použití názvu projektu k názvu souboru

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

## <a name="example-use-the-safe-project-name-for-the-namespace-name"></a>Příklad: Použití bezpečný název projektu jako název oboru názvů

Pokud chcete použít bezpečný název projektu pro obor názvů v souboru třídy C#, použijte následující syntaxi:

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

## <a name="see-also"></a>Viz také

- [Postupy: nahrazení parametrů v šabloně](how-to-substitute-parameters-in-a-template.md)
- [Přizpůsobení šablon](../ide/customizing-project-and-item-templates.md)
- [Postupy: vytváření šablon projektů](../ide/how-to-create-project-templates.md)
- [Odkaz na schéma šablony](../extensibility/visual-studio-template-schema-reference.md)
