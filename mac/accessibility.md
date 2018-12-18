---
title: Usnadnění
description: Tento článek představuje funkce pro usnadnění přístupu v sadě Visual Studio pro Mac a jak lze povolit.
author: conceptdev
ms.author: crdun
ms.date: 08/15/2017
ms.assetid: 2C4AAC2E-3B4A-4496-8BE0-1F5A7F81D1CA
ms.openlocfilehash: f90f5fca9d68ed00162fd746ddf291343c8d51f7
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296336"
---
# <a name="accessibility"></a>Usnadnění

Kromě funkcí a nástrojů v systému macOS Visual Studio for Mac má následující funkce, takže přístupnější pro osoby s postižením:

- Rozšíření text v řešení a Editor dotyková zařízení
- Možnosti změnit velikost textu v editorech
- Přizpůsobení barev v editorech
- Přizpůsobení klávesové zkratky
- Doplňování kódu pro metody a parametrů

Další informace o funkce pro usnadnění přístupu v systému macOS najdete v tématu [webu společnosti Apple](https://www.apple.com/accessibility/mac/).

## <a name="using-accessibility-features-in-visual-studio-for-mac"></a>Pomocí funkce pro usnadnění přístupu v sadě Visual Studio for Mac

Funkce usnadnění v sadě Visual Studio for Mac jsou ve výchozím nastavení vypnuta. Aby se mohly, proveďte následující kroky:

1. Přejděte na **sady Visual Studio > Předvolby > Další > usnadnění**.

2. Vyberte **povolit usnadnění** zaškrtávací políčko, jak je znázorněno v následujícím diagramu:

    ![Povolit usnadnění zaškrtávací políčko](media/accessibility-image1.png)

3. Stisknutím klávesy **restartujte Visual Studio** tlačítko Povolit funkce pro usnadnění přístupu se projeví.

Alternativně můžete použít příkazový řádek povolit funkce pro usnadnění přístupu. Provedete to tak, zadejte v terminálu následující příkaz:

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

Po zapnutí usnadnění přístupu, budete muset restartovat Visual Studio.

## <a name="how-to-use-keyboard-navigation"></a>Postupy: použití navigaci pomocí klávesnice

Navigace pomocí kláves se dá nastavit tak, že nastavíte možnost úplný přístup klávesnice **předvolby systému > klávesnice > zkratky** k **všechny ovládací prvky**:

![Panel předvoleb systémy v systému macos](media/accessibility-image2.png)

Nastavení úplné klávesnice zapne obdélník. Pak můžete vybrat pomocí ovládacích prvků:

- TAB přejděte vpřed přes ovládací prvky
- Stiskněte Shift + Tab zpětně projít ovládacích prvků
- Klávesy se šipkami pro přesun mezi ovládacími prvky směrem šipky.

Stisknutím klávesy MEZERNÍK aktivuje cílené ovládacího prvku.

## <a name="how-to-enable-and-use-voice-over"></a>Postupy: povolení a používání VoiceOver

Zapněte nebo vypněte stiskněte VoiceOver **Cmd + F5**

Procházet VoiceOver uživatelského rozhraní příkazů, použijte následující příkazy:

- Přesunutí kurzoru VoiceOver mezi ovládacími prvky: **Ctrl + Alt + šipka doleva šipka / šipka doprava**

   VoiceOver přečte název ovládací prvky, některé podrobnosti a co můžete dělat s ním.

- Zadejte skupiny a ovládací prvky (například panel řešení, nástrojů a ostatní panely): **Ctrl + Alt + Shift + šipka dolů**

   Jakmile se v ovládacím prvku, můžete použít **Ctrl + Alt + šipky** přesouvat dovnitř.

Obecné informace o používání VoiceOver v systému macOS najdete v následujících příručkách:

- [Začínáme s VoiceOver](https://help.apple.com/voiceover/info/guide/10.12/)
- [Příkazy voiceOver v systému macOS](http://lab.dotjay.com/notes/voiceover-commands/)

## <a name="see-also"></a>Viz také:

- [Funkce usnadnění v sadě Visual Studio (ve Windows)](/visualstudio/ide/reference/accessibility-features-of-visual-studio)