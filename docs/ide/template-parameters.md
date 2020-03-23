---
title: Parametry šablony projektu a položky
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "78169362"
---
# <a name="template-parameters"></a>Parametry šablony

Hodnoty v šabloně můžete nahradit při vytvoření instance šablony. Chcete-li tuto funkci nastavit, použijte *parametry šablony*. Parametry šablony lze použít k nahrazení hodnot, jako jsou názvy tříd a obory názvů v šabloně. Průvodce šablonou, který běží na pozadí, když uživatel přidá novou položku nebo projekt, nahradí tyto parametry.

## <a name="declare-and-enable-template-parameters"></a>Deklarovat a povolit parametry šablony

Parametry šablony jsou deklarovány ve formátu $*parametr*$. Například:

- $safeprojectname$

- $guid1$$guid

- $guid5$$guid5$$guid5$$guid5

### <a name="enable-parameter-substitution-in-templates"></a>Povolit nahrazení parametrů v šablonách

1. V souboru *.vstemplate* šablony vyhledejte `ProjectItem` prvek, který odpovídá položce, pro kterou chcete povolit nahrazení parametru.

1. Nastavte `ReplaceParameters` atribut prvku `ProjectItem` na `true`.

1. V souboru kódu pro položku projektu, zahrnout parametry, kde je to vhodné. Následující parametr například určuje, že pro obor názvů v souboru se používá bezpečný název projektu:

    ```csharp
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>Parametry vyhrazené šablony

V následující tabulce jsou uvedeny parametry vyhrazené šablony, které lze použít pro libovolnou šablonu:

|Parametr|Popis|
|---------------|-----------------|
|clrversion|Aktuální verze běžného jazykového běhu (CLR).|
|ext_*|Přidejte `ext_` předponu do libovolného parametru, který bude odkazovat na proměnné nadřazené šablony. Například, `ext_safeprojectname`.|
|guid[1-10]|Identifikátor GUID použitý k nahrazení identifikátoru GUID projektu v souboru projektu. Můžete zadat až 10 jedinečných identifikátorů `guid1`GUID (například ).|
|název_položky|Název souboru, ve kterém je parametr používán.|
|Machinename|Aktuální název počítače (například Computer01).|
|Projectname|Název poskytnutý uživatelem při vytvoření projektu.|
|registrovanáorganizace|Hodnota klíče registru z hklm\software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization.|
|Rootnamespace|Kořenový obor názvů aktuálního projektu. Tento parametr platí pouze pro šablony položek.|
|safeitemname|Stejné `itemname` jako se všemi nebezpečnými znaky a mezerami nahrazenými znaky podtržítka.|
|safeitemrootname|Stejné `safeitemname`jako .|
|safeprojectname|Název poskytnutý uživatelem při vytvoření projektu, ale se všemi nebezpečnými znaky a mezerami odebrány.|
|time|Aktuální čas ve formátu DD/MM/YYYY 00:00:00.|
|specifiednázev_řešení|Název řešení. Pokud je zaškrtnuto políčko „vytvořit adresář řešení“, `specifiedsolutionname` obsahuje název řešení. Pokud není zaškrtnuto políčko „vytvořit adresář řešení“, `specifiedsolutionname` je prázdné.|
|uživatelská doména|Aktuální doména uživatele.|
|uživatelské jméno|Aktuální uživatelské jméno.|
|webová_jmenovky|Název aktuálního webu. Tento parametr se používá v šabloně webového formuláře k zaručení jedinečných názvů tříd. Pokud je web v kořenovém adresáři webového serveru, tento parametr šablony se překládá do kořenového adresáře webového serveru.|
|year|Aktuální rok ve formátu YYYYY.|

> [!NOTE]
> Parametry šablony rozlišují malá a velká písmena.

## <a name="custom-template-parameters"></a>Parametry vlastní šablony

Kromě výchozích parametrů vyhrazené šablony, které se používají při výměně parametrů, můžete zadat vlastní parametry a hodnoty šablony. Další informace naleznete v [tématu CustomParameters element (Visual Studio šablony)](../extensibility/customparameters-element-visual-studio-templates.md).

## <a name="example-use-the-project-name-for-a-file-name"></a>Příklad: Použití názvu projektu pro název souboru

Názvy souborů proměnných pro položky projektu `TargetFileName` můžete zadat pomocí parametru v atributu.

Následující příklad určuje, že název spustitelného souboru používá `$projectname$`název projektu určený uživatelem .

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

## <a name="example-use-the-safe-project-name-for-the-namespace-name"></a>Příklad: Použití bezpečného názvu projektu pro název oboru názvů

Chcete-li použít bezpečný název projektu pro obor názvů v souboru třídy C#, použijte následující syntaxi:

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

Do souboru *.vstemplate* pro šablonu `ReplaceParameters="true"` projektu zahrňte atribut při odkazu na soubor:

```xml
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Viz také

- [Postup: Nahrazení parametrů v šabloně](how-to-substitute-parameters-in-a-template.md)
- [Přizpůsobení šablon](../ide/customizing-project-and-item-templates.md)
- [Postup: Vytvoření šablon projektů](../ide/how-to-create-project-templates.md)
- [Odkaz na schéma šablony](../extensibility/visual-studio-template-schema-reference.md)
