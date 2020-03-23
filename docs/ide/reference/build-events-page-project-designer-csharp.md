---
title: Stránka Události sestavení, návrhář projektu (C#)
ms.date: 10/17/2019
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- Project Designer, Build Events page
- pre-build events
- post-build events
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6629f41657a546ffb5fb48e0b6efb5f4f0dd50cb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596876"
---
# <a name="build-events-page-project-designer-c"></a>Stránka Události sestavení, návrhář projektu (C#)

Pomocí stránky **Události sestavení** **návrháře projektu** určete pokyny konfigurace sestavení. Můžete také určit podmínky, za kterých jsou spuštěny všechny události po sestavení. Další informace naleznete v [tématu How to: Specify Build Events (C#)](../../ide/how-to-specify-build-events-csharp.md) and [How to: Specify Build Events (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

**Konfigurace**

Tento ovládací prvek nelze na této stránce upravovat. Popis tohoto ovládacího prvku naleznete v tématu [Build Page, Project Designer (C#)](../../ide/reference/build-page-project-designer-csharp.md).

**Platforma**

Tento ovládací prvek nelze na této stránce upravovat. Popis tohoto ovládacího prvku naleznete v tématu [Build Page, Project Designer (C#)](../../ide/reference/build-page-project-designer-csharp.md).

**Příkazový řádek události před sestavením**

Určuje všechny příkazy, které mají být provedeny před spuštěním sestavení. Chcete-li zadat dlouhé příkazy, klepněte na **tlačítko Upravit předsestavení,** [chcete-li zobrazit dialogové okno příkazového řádku události před sestavením nebo po sestavení](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> Události předběžného sestavení se nespustí, pokud je projekt aktuální a neaktivuje se žádné sestavení.

**Příkazový řádek události po sestavení**

Určuje všechny příkazy, které mají být provedeny po ukončení sestavení. Chcete-li psát dlouhé příkazy, klepněte na **tlačítko Upravit následné sestavení** a zobrazte dialogové okno **příkazového řádku události před sestavením.**

> [!NOTE]
> Přidejte `call` příkaz před všechny příkazy po sestavení, které spouštějí soubory BAT. Příkladem je `call C:\MyFile.bat` nebo `call C:\MyFile.bat call C:\MyFile2.bat`.

**Spuštění události po sestavení**

Určuje následující podmínky pro spuštění události po sestavení, jak je znázorněno v následující tabulce.

|Možnost|Výsledek|
|------------|------------|
|**Vždy**|Událost po sestavení se spustí bez ohledu na to, zda je sestavení úspěšné.|
|**Na úspěšné sestavení**|Událost po sestavení se spustí, pokud je sestavení úspěšné. Proto bude událost spuštěna i pro projekt, který je aktuální, tak dlouho, dokud sestavení úspěšné.|
|**Když sestavení aktualizuje výstup projektu**|Událost po sestavení se spustí pouze v případě, že se výstupní soubor kompilátoru (.exe nebo .dll) liší od předchozího výstupního souboru kompilátoru. Proto událost po sestavení není spuštěna, pokud je projekt aktuální.|

## <a name="in-the-project-file"></a>V souboru projektu

V dřívějších verzích sady Visual Studio při změně nastavení **PreBuildEvent** nebo **PostBuildEvent** v ide, Visual Studio přidá `PreBuildEvent` vlastnost nebo `PostBuildEvent` do souboru projektu. Pokud je například nastavení příkazového řádku **PreBuildEvent** v prostředí IDE následující:

```input
"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"
```

pak nastavení souboru projektu je:

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)" />
</PropertyGroup>
```

Pro projekty .NET Core Visual Studio 2019 (a Visual Studio 2017 v `PreBuild` `PostBuild` novějších aktualizacích) přidá cíl MSBuild s názvem nebo pro nastavení **PreBuildEvent** a **PostBuildEvent.** Tyto cíle používají **BeforeTargets** a **AfterTargets** atributy, které MSBuild rozpozná. Například pro předchozí příklad Visual Studio nyní generuje následující kód:

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>
```

Pro událost po sestavení použijte `PostBuild` název a `AfterTargets` nastavte `PostBuildEvent`atribut na .

```xml
<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
> Tyto změny souboru projektu byly provedeny pro podporu projektů ve stylu sady SDK. Pokud migrujete soubor projektu ze starého formátu do formátu ve stylu sady `PreBuildEvent` SDK ručně, měli byste odstranit vlastnosti a `PostBuildEvent` nahradit je `PreBuild` a `PostBuild` cíle, jak je znázorněno v předchozím kódu. Informace o tom, jak zjistit, zda je projekt projektem ve stylu sady SDK, naleznete v [tématu Kontrola formátu projektu](/nuget/resources/check-project-format).

## <a name="see-also"></a>Viz také

- [Postupy: Určení událostí sestavení (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Postupy: Specifikace událostí sestavení (C#)](../../ide/how-to-specify-build-events-csharp.md)
- [Referenční dokumentace k vlastnostem projektu](../../ide/reference/project-properties-reference.md)
- [Kompilace a sestavení](../../ide/compiling-and-building-in-visual-studio.md)
