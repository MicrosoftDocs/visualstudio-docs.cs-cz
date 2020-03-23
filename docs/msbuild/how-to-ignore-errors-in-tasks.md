---
title: 'Postup: Ignorovat chyby v úkolech | Dokumenty společnosti Microsoft'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633821"
---
# <a name="how-to-ignore-errors-in-tasks"></a>Postup: Ignorovat chyby v úkolech

Někdy chcete, aby sestavení bylo tolerantní k chybám v určitých úkolech. Pokud tyto nekritické úkoly nezdaří, chcete, aby sestavení pokračovat, protože může stále produkovat požadovaný výstup. Pokud například projekt používá `SendMail` úkol k odeslání e-mailové zprávy po vytvoření každé součásti, můžete považovat za přijatelné pro sestavení pokračovat k dokončení i v případě, že poštovní servery nejsou k dispozici a stavové zprávy nelze odeslat. Nebo například pokud zprostředkující soubory jsou obvykle odstraněny během sestavení, můžete považovat za přijatelné pro sestavení pokračovat k dokončení i v případě, že tyto soubory nelze odstranit.

## <a name="use-the-continueonerror-attribute"></a>Použití atributu ContinueOnError

Atribut `ContinueOnError` prvku `Task` určuje, zda sestavení zastaví nebo pokračuje, když dojde k selhání úlohy. Tento atribut také určuje, zda jsou chyby považovány za chyby nebo upozornění při pokračování sestavení.

Atribut `ContinueOnError` může obsahovat jednu z následujících hodnot:

- **WarnAndContinue** nebo **true**. Pokud úloha selže, následné úkoly v [Target](../msbuild/target-element-msbuild.md) element a sestavení pokračovat v provádění a všechny chyby z úkolu jsou považovány za upozornění.

- **ErrorAndContinue**. Pokud úloha selže, následné `Target` úkoly v prvku a sestavení pokračovat v provádění a všechny chyby z úkolu jsou považovány za chyby.

- **ErrorAndStop** nebo **false** (výchozí). Pokud úloha selže, zbývající úkoly v elementu `Target` a sestavení nejsou `Target` provedeny a celý prvek a sestavení se považuje za neúspěšné.

Verze rozhraní .NET Framework před 4.5 `true` `false` podporovaly pouze hodnoty a.

Výchozí hodnota `ContinueOnError` je `ErrorAndStop`. Pokud nastavíte `ErrorAndStop`atribut , provedete chování explicitní pro každého, kdo čte soubor projektu.

#### <a name="to-ignore-an-error-in-a-task"></a>Ignorování chyby v úkolu

Použijte `ContinueOnError` atribut úkolu. Například:

```xml
<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>
```

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje, `Build` že cíl stále běží a sestavení je `Delete` považováno za úspěšné, i v případě, že úloha selže.

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

- [Msbuild](../msbuild/msbuild.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
