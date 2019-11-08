---
title: Akce sestavení
description: Tento článek popisuje různé akce sestavení, které lze použít pro C# projekty.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: 97cabcacf276c6972a717e968656430ad32e37e3
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73715847"
---
# <a name="build-actions"></a>Akce sestavení

Všechny soubory v projektu Visual Studio pro Mac mají akci sestavení. Určuje, co se stane se souborem během sestavení. Toto chování lze nastavit tak, že kliknete pravým tlačítkem na libovolný soubor a přejdete na **akci sestavení**, jak je znázorněno níže:

![Výběr akce kompilace sestavení z Průzkumníka řešení](media/projects-and-solutions-image1.png)

Některé běžné akce sestavení pro C# projekty jsou:

* **Žádné** – soubor není součástí sestavení jakýmkoli způsobem – je zahrnutý v projektu pro snadný přístup z rozhraní IDE.
* **Kompilovat** – soubor bude předán C# kompilátoru jako zdrojový soubor.
* **EmbeddedResource** – soubor bude předán C# kompilátoru jako prostředek, který má být vložen do sestavení. [Assembly. GetManifestResourceStream](/dotnet/api/system.reflection.assembly.getmanifestresourcestream)z oboru názvů `System.Reflection` lze použít ke čtení souboru ze sestavení.
* **Obsah** – pro projekty ASP.NET budou tyto soubory zahrnuty jako součást webu při jeho nasazení. Pro projekty Xamarin. iOS a Xamarin. Mac budou zahrnuty do sady prostředků aplikace.

Je možné vybrat více než jeden soubor v Průzkumníku řešení, což vám umožní nastavit akci sestavení na mnoho souborů najednou.

K dispozici jsou také akce sestavení pro konkrétní projekty. Projekty Xamarin. iOS mají akci sestavení **BundleResource** , která tento soubor přidá jako součást sady prostředků aplikace. Informace o akcích sestavení specifických pro Xamarin. Android najdete v průvodci [procesem sestavení](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions) .

## <a name="see-also"></a>Viz také:

- [Akce sestavení (Visual Studio ve Windows)](/visualstudio/ide/build-actions)