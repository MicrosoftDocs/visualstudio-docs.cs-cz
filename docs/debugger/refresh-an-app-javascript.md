---
title: Aktualizace aplikace pro UWP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- JavaScript debugging, refreshing pages [UWP apps]
- debugging, refreshing pages [UWP apps]
- DOM Explorer, Refresh [UWP apps]
- Refresh [UWP apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- uwp
ms.openlocfilehash: 0b1d19c0b607d2c5a09fddc9d4550230e478d57a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730312"
---
# <a name="refresh-a-uwp-app-in-visual-studio"></a>Aktualizace aplikace pro UWP v aplikaci Visual Studio

 Během ladění můžete provádět změny kódu a pak aplikaci pro UWP aktualizovat pomocí JavaScriptu tak, že kliknete na tlačítko **aktualizovat aplikaci pro Windows** na panelu nástrojů **ladění** . Kliknutím na toto tlačítko se aplikace znovu načte bez zastavení a restartování ladicího programu. Funkce aktualizovat umožňuje upravit kód HTML, CSS a JavaScript a rychle zobrazit výsledek. Tato funkce je podporovaná pro aplikace pro UWP.

 Aktualizace neudržuje stav aplikace nebo odráží následující změny vaší aplikace:

- Změny souborů manifestu balíčku, včetně změn imagí zadaných v manifestu balíčku.

- Referenční změny, jako je například přidání nebo odebrání odkazu na sadu SDK nebo změny prostředí Windows Runtimech komponent (soubory. winmd).

- Změny prostředků, jako jsou například změny v řetězcích souborů. resjson.

- Změny souborů projektu, které mají za následek změny názvu cesty, nové soubory projektu nebo odstraněné soubory.

- Změny vlastností projektu a položky, jako jsou například změny vybraného ladicího zařízení, nebo změny pro akci balíčku pro soubor (v okno Vlastnosti).

> [!IMPORTANT]
> Když změníte odkazy, změníte manifest balíčku nebo provedete jiné změny uvedené v předchozím seznamu, je nutné zastavit a znovu spustit ladicí program, aby bylo možné aktualizovat zdrojové soubory HTML, CSS a JavaScript.

### <a name="to-refresh-an-app"></a>Aktualizace aplikace

1. V projektu UWP otevřeném v aplikaci Visual Studio vyberte jako cíl ladění **místní počítač** .

     ![Vybrat cílový seznam pro ladění](../debugger/media/js_select_target.png "JS_Select_Target")

3. Stisknutím klávesy F5 spusťte aplikaci v režimu ladění.

4. Přepněte do sady Visual Studio.

5. Na domovské stránce vaší aplikace pro UWP upravte některé z těchto HTML.

7. Klikněte na tlačítko **aktualizovat aplikaci pro Windows** , které vypadá takto: ![tlačítko Aktualizovat aplikaci pro Windows](../debugger/media/js_refresh.png "JS_Refresh"). (Nebo stiskněte F4.)

8. Přepněte do aplikace. Aplikace se znovu načte a k vykreslení aplikace se použije aktualizovaný kód HTML.

## <a name="see-also"></a>Viz také:
- [Rychlý start: Ladění kódu HTML a CSS](../debugger/quickstart-debug-html-and-css.md)