---
title: 'Postupy: ignorování chyb v úlohách | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild - "vs-ide-sdk"
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, ignoring errors
- ContinueOnError attribute [MSBuild]
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
author: mikejo5000
ms.author: mikejo
manager: douge
ms.openlocfilehash: 3df3a3b40dd67f12bac19f4e69f5293c85bb85f3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940031"
---
# <a name="how-to-ignore-errors-in-tasks"></a>Postupy: ignorování chyb v úlohách
Občas můžete chtít sestavení bude odolný vůči chybám chyb v určité úlohy. Pokud tyto méně náročné úlohy nezdaří, chcete pokračovat, protože stále může vytvořit požadovaný výstupní sestavení. Například, pokud projekt používá `SendMail` úloha pro odeslání e-mailovou zprávu po jednotlivých komponent je sestavená, můžete zvážit je přijatelné pro sestavení a pokračujte na dokončení, i když nedostupné servery e-mailu a stavové zprávy nelze odeslat. Nebo, například pokud zprostředkující soubory jsou obvykle odstraněny během sestavení, můžete zvážit je přijatelné pro sestavení a pokračujte na dokončení, i v případě, že tyto soubory nelze odstranit.  
  
## <a name="use-the-continueonerror-attribute"></a>Použití ContinueOnError – atribut  
 `ContinueOnError` Atribut `Task` element určuje, zda sestavení zastaví nebo bude pokračovat, dojde k selhání úlohy. Tento atribut také určuje, zda chyby jsou považované za chyby nebo upozornění, když sestavení dál.  
  
 `ContinueOnError` Atribut může obsahovat jednu z následujících hodnot:  
  
- **WarnAndContinue** nebo **true**. Při selhání úkolu, následné úlohy v [cílové](../msbuild/target-element-msbuild.md) elementu a sestavení budou dál spouštět a všechny chyby z úlohy jsou považovány za upozornění.  
  
- **ErrorAndContinue**. Při selhání úkolu, následné úlohy v `Target` elementu a sestavení budou dál spouštět a všechny chyby z úlohy jsou považována za chyby.  
  
- **ErrorAndStop** nebo **false** (výchozí). Při selhání úkolu, ve zbývajících úkolech v `Target` elementu a sestavení nejsou provedeny a celé `Target` elementu a sestavení se považuje za neúspěšný.  
  
  Verze rozhraní .NET Framework před 4.5 podporována pouze `true` a `false` hodnoty.  
  
  Výchozí hodnota `ContinueOnError` je `ErrorAndStop`. Pokud nastavíte atribut na `ErrorAndStop`, provedete chování explicitní každý, kdo čte soubor projektu.  
  
#### <a name="to-ignore-an-error-in-a-task"></a>Chcete-li ignorovat chybu v rámci úlohy  
  
-   Použití `ContinueOnError` atribut úkolu. Příklad:  
  
     `<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>`  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, že `Build` cíl stále spuštěný a úspěchu, i když se považuje za sestavení `Delete` úloh selže.  
  
```xml  
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
  
## <a name="see-also"></a>Viz také:
[MSBuild](../msbuild/msbuild.md)  
[Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)   
[Úlohy](../msbuild/msbuild-tasks.md)