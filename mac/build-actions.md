---
title: Akce sestavení
description: Tento článek popisuje různé akce sestavení, které lze použít pro projekty jazyka C#
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: d089f38bd91eda2565f215e8d15a74cc119b8767
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "73714400"
---
# <a name="build-actions"></a>Akce sestavení

Všechny soubory v projektu Visual Studio for Mac mají akci sestavení. Akce sestavení řídí, co se stane se souborem během sestavení. 

>[!NOTE]
>Toto téma se týká Visual Studia pro Mac. Visual Studio ve Windows najdete v tématu [Sestavení akcí](/visualstudio/ide/build-actions).

## <a name="set-a-build-action"></a>Nastavení akce sestavení

Pokud chcete nastavit akci sestavení pro soubor v Visual Studiu for Mac, můžete kliknout pravým tlačítkem myši na libovolný soubor a přejít na **Vytvořit akci**, jak je znázorněno níže:

![Výběr akce sestavení kompilace z průzkumníka řešení](media/projects-and-solutions-image1.png)

Akce sestavení pro tento soubor se zobrazí v informační nabídce. 

## <a name="build-action-values"></a>Vytváření hodnot akcí

Některé běžné akce sestavení pro projekty, které můžete vytvořit ve Visual Studiu pro Mac, zahrnují:

|Vytvořit akci | Typy projektů | Popis |
|--|--|--|
| **Kompilaci** | jakékoli | Soubor je předán kompilátoru Jazyka C# jako zdrojový soubor.|
| **Obsah** | .NET, Xamarin | U ASP.NET projektů jsou tyto soubory zahrnuty jako součást webu při jeho nasazení. U projektů Xamarin.iOS a Xamarin.Mac budou zahrnuty do balíčku aplikací.|
| **Vložený prostředek** | .NET | Soubor je předán kompilátoru Jazyka C# jako prostředek, který má být vložen do sestavení. [Assembly.GetManifestResourceStream](/dotnet/api/system.reflection.assembly.getmanifestresourcestream), `System.Reflection` z oboru názvů, lze potom ke čtení souboru ze sestavení.|
| **Žádné** | jakékoli | Soubor není součástí sestavení v žádném případě a je součástí projektu pro snadný přístup z ide. Tuto hodnotu lze použít například pro soubory dokumentace, jako jsou soubory "ReadMe".|

> [!NOTE]
> Další akce sestavení mohou být definovány pro konkrétní typy projektů, takže seznam akcí sestavení závisí na typu projektu a hodnoty, které nejsou v tomto seznamu.  

Projekty Xamarin.iOS mají akci **sestavení sady BundleResource,** která přidá soubor jako součást balíčku aplikace. Informace o akcích sestavení specifických pro Xamarin.Android najdete v průvodci [procesem sestavení.](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions)

Je také možné vybrat více než jeden soubor v průzkumníku řešení, což vám umožní nastavit akci sestavení na mnoho souborů najednou.

## <a name="see-also"></a>Viz také

- [Akce sestavení (Visual Studio ve Windows)](/visualstudio/ide/build-actions)