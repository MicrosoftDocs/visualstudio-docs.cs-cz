---
title: 'Postupy: ignorování chyb v úlohách | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, ignoring errors
- ContinueOnError attribute [MSBuild]
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: abd907e86a451ca035d44d9a12084c7b84acd1ed
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777891"
---
# <a name="how-to-ignore-errors-in-tasks"></a>Postupy: ignorování chyb v úlohách
Někdy je vhodné, aby bylo sestavení odolné vůči chybám v určitých úlohách. Pokud tyto nekritické úkoly selžou, chcete, aby sestavení pokračovalo, protože stále může vytvořit požadovaný výstup. Například pokud projekt používá úlohu `SendMail` k odeslání e-mailové zprávy po sestavení každé součásti, může být vhodné, aby sestavení bylo přijatelné i v případě, že poštovní servery nejsou k dispozici a nelze odeslat stavové zprávy. Nebo například pokud jsou během sestavení obvykle smazány mezilehlé soubory, může být vhodné, aby sestavení bylo přijatelné i v případě, že tyto soubory nelze odstranit.

## <a name="use-the-continueonerror-attribute"></a>Použití atributu ContinueOnError
Atribut `ContinueOnError` elementu `Task` určuje, zda je sestavení zastaveno nebo pokračuje, když dojde k selhání úlohy. Tento atribut také určuje, zda jsou chyby považovány za chyby nebo upozornění, když sestavení pokračuje.

Atribut `ContinueOnError` může obsahovat jednu z následujících hodnot:

- **WarnAndContinue** nebo **true**. Pokud se úloha nezdařila, následné úkoly v [cílovém](../msbuild/target-element-msbuild.md) elementu a sestavení se budou dále spouštět a všechny chyby z tohoto úkolu jsou považovány za upozornění.

- **ErrorAndContinue**. Pokud se úloha nezdařila, následné úkoly v prvku `Target` a sestavení se budou dále spouštět a všechny chyby z tohoto úkolu jsou považovány za chyby.

- **ErrorAndStop** nebo **false** (výchozí). Pokud se úloha nezdařila, zbývající úkoly v prvku `Target` a sestavení nejsou provedeny a celý `Target` element a sestavení se považuje za neúspěšné.

Verze .NET Framework před 4,5 podporují pouze hodnoty `true` a `false`.

Výchozí hodnota `ContinueOnError` je `ErrorAndStop`. Pokud nastavíte atribut na `ErrorAndStop`, uděláte chování explicitně pro kohokoli, kdo soubor projektu přečte.

#### <a name="to-ignore-an-error-in-a-task"></a>Ignorování chyby v úloze

Použijte atribut `ContinueOnError` úlohy. Příklad:

```c#
<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>
```

## <a name="example"></a>Příklad
Následující příklad kódu ukazuje, že cílový `Build` stále běží a sestavení je považováno za úspěšné, i když se úloha `Delete` nezdařila.

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
- [MSBuild](../msbuild/msbuild.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
