---
title: Parametry šablony | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
ms.assetid: 1b567143-08c6-4d7a-b484-49f0671754fe
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2d7bb7e0f3dfee3dd1bf3e9b42afd5837a29f6ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646810"
---
# <a name="template-parameters"></a>Parametry šablony
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí parametrů v šablonách lze při vytváření instance šablony nahradit hodnoty nejdůležitějších částí šablony, jako jsou názvy tříd a obory názvů. Tyto parametry jsou nahrazeny průvodcem šablon, který běží na pozadí, když uživatel klikne na **tlačítko OK** v dialogových oknech **Nový projekt** nebo **Přidat novou položku** .

## <a name="declaring-and-enabling-template-parameters"></a>Deklarování a povolování parametrů šablony
 Parametry šablony jsou deklarovány ve formátu $*Parameter*$. Příklad:

- $safeprojectname $

- $guid $1

- $guid $5

#### <a name="to-enable-parameter-substitution-in-templates"></a>Povolení nahrazování parametrů v šablonách

1. V souboru .vstemplate šablony vyhledejte prvek `ProjectItem`, který odpovídá položce, pro kterou chcete povolit náhradu parametrů.

2. Nastavte `ReplaceParameters` atribut `ProjectItem` elementu na `true` .

3. V souboru kódu pro položku projektu zadejte parametry tam, kde je to vhodné. Například následující parametr určuje, že název bezpečného projektu je použit pro obor názvů v souboru:

    ```
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>Rezervované parametry šablony
 Následující tabulka uvádí seznam rezervovaných parametrů šablony, které mohou být použity libovolnou šablonou.

> [!NOTE]
> Parametry šablony rozlišují velká a malá písmena.

|Parametr|Popis|
|---------------|-----------------|
|`clrversion`|Aktuální verze modulu CLR (Common Language Runtime).|
|`GUID [1-10]`|Identifikátor GUID, který slouží k nahrazení identifikátoru GUID projektu v souboru projektu. Můžete zadat až 10 jedinečných identifikátorů GUID (například `guid1)` .|
|`itemname`|Název zadaný uživatelem v dialogovém okně **Přidat novou položku** .|
|`machinename`|Aktuální název počítače (například Computer01).|
|`projectname`|Název zadaný uživatelem v dialogovém okně **Nový projekt** .|
|`registeredorganization`|Hodnota klíče registru z HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization.|
|`rootnamespace`|Kořenový obor názvů aktuálního projektu Tento parametr platí pouze pro šablony položek.|
|`safeitemname`|Jméno zadané uživatelem v dialogovém okně **Přidat novou položku** , které odeberou všechny nezabezpečené znaky a mezery.|
|`safeprojectname`|Název zadaný uživatelem v dialogovém okně **Nový projekt** s odebranými nebezpečnými znaky a mezerami.|
|`time`|Aktuální čas ve formátu DD/MM/RRRR 00:00:00.|
|`SpecificSolutionName`|Název řešení. Pokud je zaškrtnuto políčko „vytvořit adresář řešení“, `SpecificSolutionName` obsahuje název řešení. Pokud není zaškrtnuto políčko „vytvořit adresář řešení“, `SpecificSolutionName` je prázdné.|
|`userdomain`|Aktuální doména uživatele.|
|`username`|Aktuální uživatelské jméno.|
|`webnamespace`|Název aktuálního webu. Tento parametr se používá v šabloně webového formuláře k zaručení jedinečných názvů tříd. Pokud se web nachází v kořenovém adresáři webového serveru, tento parametr šablony se přeloží do kořenového adresáře webového serveru.|
|`year`|Aktuální rok ve formátu YYYY.|

## <a name="custom-template-parameters"></a>Parametry vlastní šablony
 Kromě výchozích parametrů vyhrazené šablony, které se používají při nahrazování parametrů, můžete zadat vlastní parametry a hodnoty šablon. Další informace naleznete v tématu [CustomParameters – element (šablony sady Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)

## <a name="example-replacing-files-names"></a>Příklad: Nahrazení názvů souborů
 Můžete zadat názvy souborů proměnných pro položky projektu pomocí parametru s `TargetFileName` atributem. Například můžete určit, že soubor. exe použije název projektu, který je určen `$projectname$` jako název souboru.

```
<TemplateContent>
    <ProjectItem
        ReplaceParameters="true"
        TargetFileName="$projectname$.exe">
            File1.exe
    </ProjectItem>
      ...
</TemplateContent>
```

## <a name="example-using-the-project-name-for-the-namespace-name"></a>Příklad: Použití názvu projektu jako název oboru názvů
 Chcete-li použít název projektu pro obor názvů v souboru třídy jazyka Visual C# Class1.cs, použijte následující syntaxi:

```
#region Using directives

using System;
using System.Collections.Generic;
using System.Text;

#endregion

namespace $safeprojectname$
{
    public class Class1
        {
            public Class1()
                {

                }
         }
}
```

 V souboru. vstemplate pro šablonu projektu zahrňte při odkazování na soubor Class1.cs následující kód XML:

```
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Viz také
 [Přizpůsobení šablon](../ide/customizing-project-and-item-templates.md)
