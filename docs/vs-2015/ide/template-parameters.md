---
title: Parametry šablony | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
ms.assetid: 1b567143-08c6-4d7a-b484-49f0671754fe
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ef4e1a6e3c56df744ce5375a1cb3a1dbd53a6fad
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49238898"
---
# <a name="template-parameters"></a>Parametry šablony
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí parametrů v šablonách lze při vytváření instance šablony nahradit hodnoty nejdůležitějších částí šablony, jako jsou názvy tříd a obory názvů. Tyto parametry jsou nahrazené Průvodce šablonou, která běží na pozadí, když uživatel klikne **OK** v **nový projekt** nebo **přidat novou položku** dialogových oknech.  
  
## <a name="declaring-and-enabling-template-parameters"></a>Deklarace a povolení parametry šablony  
 Parametry šablon jsou deklarovány ve formátu $*parametr*$. Příklad:  
  
-   $safeprojectname$  
  
-   $guid1$  
  
-   $guid5$  
  
#### <a name="to-enable-parameter-substitution-in-templates"></a>Povolit nahrazení parametrů v šablonách  
  
1.  V souboru .vstemplate šablony vyhledejte prvek `ProjectItem`, který odpovídá položce, pro kterou chcete povolit náhradu parametrů.  
  
2.  Nastavte `ReplaceParameters` atribut `ProjectItem` elementu `true`.  
  
3.  V souboru kódu pro položku projektu zahrnují parametry, kde je to vhodné. Například následující parametr určuje, že název projektu bezpečně použít pro obor názvů v souboru:  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
## <a name="reserved-template-parameters"></a>Vyhrazené parametry šablon  
 Následující tabulka uvádí vyhrazené parametry šablon, které mohou využívat všechny šablony.  
  
> [!NOTE]
>  Parametry šablony jsou malá a velká písmena.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`clrversion`|Aktuální verze modulu common language runtime (CLR).|  
|`GUID [1-10]`|GUID, který se používá k nahrazení identifikátoru GUID projektu v souboru projektu. Můžete zadat až 10 jedinečných identifikátorů GUID (například `guid1)`.|  
|`itemname`|Název zadaný uživatelem v **přidat novou položku** dialogové okno.|  
|`machinename`|Aktuální název počítače (například Computer01).|  
|`projectname`|Název zadaný uživatelem v **nový projekt** dialogové okno.|  
|`registeredorganization`|Hodnotu klíče registru z HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization.|  
|`rootnamespace`|Kořenový obor názvů aktuálního projektu. Tento parametr platí pouze pro šablony položek.|  
|`safeitemname`|Název zadaný uživatelem v **přidat novou položku** dialogovém okně se všemi problematické znaky a byly odebrány mezery.|  
|`safeprojectname`|Název zadaný uživatelem v **nový projekt** dialogovém okně se všemi problematické znaky a byly odebrány mezery.|  
|`time`|Aktuální čas ve formátu DD/MM/RRRR 00:00:00.|  
|`SpecificSolutionName`|Název řešení. Pokud je zaškrtnuto políčko „vytvořit adresář řešení“, `SpecificSolutionName` obsahuje název řešení. Pokud není zaškrtnuto políčko „vytvořit adresář řešení“, `SpecificSolutionName` je prázdné.|  
|`userdomain`|Aktuální uživatel domény.|  
|`username`|Aktuální uživatelské jméno.|  
|`webnamespace`|Název aktuálního webu. Tento parametr se používá v šabloně webového formuláře zajistit jedinečné názvy tříd. Pokud webový server je v kořenovém adresáři webovým serverem, tento parametr šablony přeloží do kořenového adresáře na webovém serveru.|  
|`year`|Aktuální rok ve formátu RRRR.|  
  
## <a name="custom-template-parameters"></a>Parametry vlastní šablony  
 Můžete určit vlastní parametry a hodnoty šablony, kromě vyhrazených výchozích parametrů šablony, které se používají při nahrazení parametru. Další informace najdete v tématu [CustomParameters – Element (šablony sady Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)  
  
## <a name="example-replacing-files-names"></a>Příklad: Nahrazení názvů souborů  
 Můžete zadat různé názvy souborů pro položky projektu pomocí parametru s `TargetFileName` atribut. Například můžete zadat, že soubor .exe použít název projektu, určené `$projectname$`, jako je název souboru.  
  
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
 Použití názvu projektu pro obor názvů v jazyce Visual C# třídy souboru Class1.cs, použijte následující syntaxi:  
  
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
  
 V souboru .vstemplate šablony projektu zahrnují následující kód XML, když odkazujete na soubor Class1.cs:  
  
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



