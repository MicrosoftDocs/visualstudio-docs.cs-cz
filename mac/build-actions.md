---
title: Akce sestavení
description: Tento článek popisuje různé akce sestavení, které lze použít pro projekty v jazyce C#.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: d089f38bd91eda2565f215e8d15a74cc119b8767
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "73714400"
---
# <a name="build-actions"></a>Akce sestavení

Všechny soubory v projektu Visual Studio pro Mac mají akci sestavení. Akce sestavení Určuje, co se stane se souborem během sestavení. 

>[!NOTE]
>Toto téma se týká Visual Studio pro Mac. V případě sady Visual Studio ve Windows, přečtěte si téma [Akce sestavení](/visualstudio/ide/build-actions).

## <a name="set-a-build-action"></a>Nastavit akci sestavení

Chcete-li nastavit akci sestavení pro soubor v Visual Studio pro Mac, můžete kliknout pravým tlačítkem na libovolný soubor a procházet k **akci sestavení**, jak je znázorněno níže:

![Výběr akce kompilace sestavení z Průzkumníka řešení](media/projects-and-solutions-image1.png)

Akce sestavení pro tento soubor se zobrazí v rozevírací nabídce. 

## <a name="build-action-values"></a>Sestavit hodnoty akcí

Některé běžné akce sestavení pro projekty, které můžete sestavit v Visual Studio pro Mac zahrnují:

|Akce sestavení | Typy projektů | Popis |
|--|--|--|
| **Sestavení** | Libovolný | Soubor je předán kompilátoru C# jako zdrojový soubor.|
| **Obsah** | .NET, Xamarin | Pro projekty ASP.NET jsou tyto soubory zahrnuty jako součást webu při jeho nasazení. Pro projekty Xamarin. iOS a Xamarin. Mac budou zahrnuty do sady prostředků aplikace.|
| **Vložený prostředek** | .NET | Soubor je předán kompilátoru jazyka C# jako prostředek, který má být vložen do sestavení. [Assembly. GetManifestResourceStream](/dotnet/api/system.reflection.assembly.getmanifestresourcestream)z `System.Reflection` oboru názvů pak lze použít ke čtení souboru ze sestavení.|
| **Žádný** | Libovolný | Soubor není součástí sestavení jakýmkoli způsobem a je součástí projektu pro snadný přístup z integrovaného vývojového prostředí (IDE). Tato hodnota se dá použít například pro soubory dokumentace, například soubory Readme.|

> [!NOTE]
> Další akce sestavení mohou být definovány pro konkrétní typy projektů, takže seznam akcí sestavení závisí na typu projektu a hodnoty mohou být zobrazeny, které nejsou v tomto seznamu.  

Projekty Xamarin. iOS mají akci sestavení **BundleResource** , která tento soubor přidá jako součást sady prostředků aplikace. Informace o akcích sestavení specifických pro Xamarin. Android najdete v průvodci [procesem sestavení](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions) .

Je také možné vybrat více než jeden soubor v Průzkumníku řešení, což vám umožní nastavit akci sestavení na mnoho souborů najednou.

## <a name="see-also"></a>Viz také

- [Akce sestavení (Visual Studio ve Windows)](/visualstudio/ide/build-actions)