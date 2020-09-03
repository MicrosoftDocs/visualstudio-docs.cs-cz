---
title: 'Postupy: ignorování chyb v úlohách | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, ignoring errors
- ContinueOnError attribute [MSBuild]
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
author: ghogen
ms.author: ghogen
manager: jillfra
ms.openlocfilehash: 9899b7367e6ae9255755ae04fe06d8c8733043ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77633821"
---
# <a name="how-to-ignore-errors-in-tasks"></a>Postupy: ignorování chyb v úlohách

Někdy je vhodné, aby bylo sestavení odolné vůči chybám v určitých úlohách. Pokud tyto nekritické úkoly selžou, chcete, aby sestavení pokračovalo, protože stále může vytvořit požadovaný výstup. Například pokud projekt používá `SendMail` úlohu k odeslání e-mailové zprávy po sestavení každé součásti, může být vhodné, aby bylo sestavení přijatelné, i když poštovní servery nejsou k dispozici a nelze odeslat stavové zprávy. Nebo například pokud jsou během sestavení obvykle smazány mezilehlé soubory, může být vhodné, aby sestavení bylo přijatelné i v případě, že tyto soubory nelze odstranit.

## <a name="use-the-continueonerror-attribute"></a>Použití atributu ContinueOnError

`ContinueOnError`Atribut `Task` elementu určuje, zda je sestavení zastaveno nebo pokračuje, když dojde k selhání úlohy. Tento atribut také určuje, zda jsou chyby považovány za chyby nebo upozornění, když sestavení pokračuje.

`ContinueOnError`Atribut může obsahovat jednu z následujících hodnot:

- **WarnAndContinue** nebo **true**. Pokud se úloha nezdařila, následné úkoly v [cílovém](../msbuild/target-element-msbuild.md) elementu a sestavení se budou dále spouštět a všechny chyby z tohoto úkolu jsou považovány za upozornění.

- **ErrorAndContinue**. Pokud se úloha nezdařila, následné úkoly v `Target` elementu a sestavení se budou dále spouštět a všechny chyby z tohoto úkolu jsou považovány za chyby.

- **ErrorAndStop** nebo **false** (výchozí). Pokud se úloha nepovede, zbývající úkoly v `Target` elementu a sestavení se nezpracují a celý `Target` element a sestavení se považuje za neúspěšné.

Verze .NET Framework před 4,5 podporovaly pouze `true` `false` hodnoty a.

Výchozí hodnota `ContinueOnError` je `ErrorAndStop` . Pokud nastavíte atribut na `ErrorAndStop` , můžete chování provést explicitně pro kohokoli, kdo soubor projektu přečte.

#### <a name="to-ignore-an-error-in-a-task"></a>Ignorování chyby v úloze

Použijte `ContinueOnError` atribut Task. Příklad:

```xml
<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>
```

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje, že `Build` cíl stále běží a sestavení je považováno za úspěšné, i když `Delete` úloha neproběhne úspěšně.

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

## <a name="see-also"></a>Viz také

- [Nástroji](../msbuild/msbuild.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
