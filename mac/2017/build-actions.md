---
title: Akce sestavení
description: Tento článek popisuje různé akce sestavení, které lze použít pro projekty jazyka C#
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: d55ab6aea15dbad7f1cbd718136fba261dfa1c69
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983259"
---
# <a name="build-actions"></a>Akce sestavení

Všechny soubory v projektu Visual Studio for Mac mají akci sestavení. Určuje, co se stane se souborem během sestavení. Toto chování lze nastavit kliknutím pravým tlačítkem myši na libovolný soubor a procházením **položky Build Action**, jak je znázorněno níže:

![Výběr akce sestavení kompilace z průzkumníka řešení](media/projects-and-solutions-image1.png)

Některé běžné akce sestavení pro projekty Jazyka C# jsou:

* **Žádný** – soubor není součástí sestavení v žádném případě – je součástí projektu pro snadný přístup z ide.
* **Kompilace** - Soubor bude předán kompilátoru Jazyka C# jako zdrojový soubor.
* **EmbeddedResource** - Soubor bude předán kompilátoru Jazyka C# jako prostředek, který má být vložen do sestavení. [Assembly.GetManifestResourceStream](/dotnet/api/system.reflection.assembly.getmanifestresourcestream), `System.Reflection` z oboru názvů, lze potom ke čtení souboru ze sestavení.
* **Obsah** – pro ASP.NET projekty budou tyto soubory zahrnuty jako součást webu při jeho nasazení. U projektů Xamarin.iOS a Xamarin.Mac budou zahrnuty do balíčku aplikací.

V průzkumníku řešení je možné vybrat více než jeden soubor, což vám umožní nastavit akci sestavení na mnoho souborů najednou.

Existují také akce sestavení pro konkrétní projekty. Projekty Xamarin.iOS mají akci **sestavení sady BundleResource,** která přidá soubor jako součást balíčku aplikace. Informace o akcích sestavení specifických pro Xamarin.Android najdete v průvodci [procesem sestavení.](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions)

## <a name="see-also"></a>Viz také

- [Akce sestavení (Visual Studio ve Windows)](/visualstudio/ide/build-actions)