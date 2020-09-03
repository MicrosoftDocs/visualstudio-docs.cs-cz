---
title: 'Postupy: ignorování chyb v úlohách | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, ignoring errors
- ContinueOnError attribute [MSBuild]
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5025cc3e9dc0e13c3ae4658d129f5d0ac94f6fd6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156591"
---
# <a name="how-to-ignore-errors-in-tasks"></a>Postupy: Ignorování chyb v úlohách
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Někdy je vhodné, aby bylo sestavení odolné vůči chybám v určitých úlohách. Pokud tyto nekritické úkoly selžou, chcete, aby sestavení pokračovalo, protože stále může vytvořit požadovaný výstup. Například pokud projekt používá `SendMail` úlohu k odeslání e-mailové zprávy po sestavení každé součásti, může být vhodné, aby bylo sestavení přijatelné, i když poštovní servery nejsou k dispozici a nelze odeslat stavové zprávy. Nebo například pokud jsou během sestavení obvykle smazány mezilehlé soubory, může být vhodné, aby sestavení bylo přijatelné i v případě, že tyto soubory nelze odstranit.  
  
## <a name="using-the-continueonerror-attribute"></a>Použití atributu ContinueOnError  
 `ContinueOnError`Atribut `Task` elementu určuje, zda je sestavení zastaveno nebo pokračuje, když dojde k selhání úlohy. Tento atribut také určuje, zda jsou chyby považovány za chyby nebo upozornění, když sestavení pokračuje.  
  
 `ContinueOnError`Atribut může obsahovat jednu z následujících hodnot:  
  
- **WarnAndContinue** nebo **true**. Pokud se úloha nezdařila, následné úkoly v [cílovém](../msbuild/target-element-msbuild.md) elementu a sestavení se budou dále spouštět a všechny chyby z tohoto úkolu jsou považovány za upozornění.  
  
- **ErrorAndContinue**. Pokud se úloha nezdařila, následné úkoly v `Target` elementu a sestavení se budou dále spouštět a všechny chyby z tohoto úkolu jsou považovány za chyby.  
  
- **ErrorAndStop** nebo **false** (výchozí). Pokud se úloha nepovede, zbývající úkoly v `Target` elementu a sestavení se nezpracují a celý `Target` element a sestavení se považuje za neúspěšné.  
  
  Verze .NET Framework před 4,5 podporovaly pouze `true` `false` hodnoty a.  
  
  Výchozí hodnota `ContinueOnError` je `ErrorAndStop` . Pokud nastavíte atribut na `ErrorAndStop` , můžete chování provést explicitně pro kohokoli, kdo soubor projektu přečte.  
  
#### <a name="to-ignore-an-error-in-a-task"></a>Ignorování chyby v úloze  
  
- Použijte `ContinueOnError` atribut Task. Příklad:  
  
     `<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>`  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, že `Build` cíl stále běží a sestavení je považováno za úspěšné, i když `Delete` úloha neproběhne úspěšně.  
  
```  
<Project DefaultTargets="FakeBuild"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Files Include="*.obj"/>  
    </ItemGroup>  
    <Target Name="Clean">  
        <Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>  
    </Target>  
  
    <Target Name="FakeBuild" DependsOnTargets="Clean">  
        <Message Text="Building after cleaning..."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Viz také
[Nástroji](msbuild.md)  
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)   
 [Úlohy](../msbuild/msbuild-tasks.md)
