---
title: Přístupnost
description: Tento článek představuje funkce usnadnění v sadě Visual Studio pro Mac a jak je lze povolit.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 08/15/2017
ms.assetid: 2C4AAC2E-3B4A-4496-8BE0-1F5A7F81D1CA
ms.openlocfilehash: c0f056643a8cea0c9a5eca9801d2bd008e0793a8
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "79301683"
---
# <a name="accessibility"></a>Přístupnost

Kromě funkcí a nástrojů v systému macOS má Visual Studio pro Mac následující funkce, díky čemuž je přístupnější pro osoby s postižením:

- Zvětšení textu v panelech řešení a editoru
- Možnosti velikosti textu v editorech
- Přizpůsobení barev v editorech
- Přizpůsobení klávesových zkratek
- Dokončení kódu pro metody a parametry

Další informace o funkcích usnadnění v macOS najdete na [webu Apple](https://www.apple.com/accessibility/mac/).

## <a name="using-accessibility-features-in-visual-studio-for-mac"></a>Používání funkcí usnadnění ve Visual Studiu pro Mac

Funkce usnadnění v Sadě Visual Studio pro Mac jsou ve výchozím nastavení vypnuté. Chcete-li je povolit, proveďte následující kroky:

1. Přejděte na **předvolby > sady Visual Studio > další > usnadnění přístupu**.

2. Zaškrtněte políčko **Povolit usnadnění,** jak je znázorněno na následujícím diagramu:

    ![Zaškrtávací políčko Povolit usnadnění přístupu](media/accessibility-image1.png)

3. Stisknutím tlačítka **Restartovat visual studio** povolíte, aby se funkce usnadnění projevily.

Případně můžete pomocí příkazového řádku povolit funkce usnadnění přístupu. Chcete-li to provést, zadejte do terminálu následující příkaz:

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

Po zapnutí usnadnění přístupu je třeba restartovat visual studio.

## <a name="how-to-use-keyboard-navigation"></a>Postup: Použití navigace pomocí klávesnice

Navigaci pomocí klávesnice lze povolit nastavením možnosti Úplný přístup pomocí klávesnice v **předvolbách systému > klávesové zkratky > klávesové zkratky** pro **všechny ovládací prvky**:

![Panel Předvoleb systémů v systému macos](media/accessibility-image2.png)

Nastavení úplného přístupu pomocí klávesnice zapne obdélník fokusu. Ovládací prvky pak můžete vybrat pomocí:

- Tabulátorem pro procházení ovládacích prvků
- Shift-Tab pro přechod dozadu přes ovládací prvky
- Šipky pro pohyb mezi ovládacími prvky ve směru šipek.

Stisknutím mezerníku se aktivuje zaostřený ovládací prvek.

## <a name="how-to-enable-and-use-voice-over"></a>Postup: Povolení a používání funkce Voice Over

Zapnutí nebo vypnutí voiceoveru stiskněte **tlačítko Cmd + F5**

Chcete-li procházet příkazy UI VoiceOver, použijte následující příkazy:

- Přesunout kurzor VoiceOveru mezi ovládacími prvky: **Ctrl + Alt + šipka doleva / šipka doprava**

   VoiceOver přečte název ovládacích prvků, některé podrobnosti o něm a co s ním můžete dělat.

- Zadejte skupiny a ovládací prvky (například panel řešení, panel nástrojů a další podložky): **Ctrl + Alt + Shift + Šipka dolů**

   Jakmile jste uvnitř ovládacího prvku, můžete se pohybovat uvnitř **ovládacího prvku pomocí kláves Ctrl + Alt +.**

Obecné informace o používání VoiceOveru v macOS najdete v následujících průvodcích:

- [Začínáme s VoiceOverem](https://help.apple.com/voiceover/info/guide/10.12/)
- [Příkazy VoiceOveru v macOS](https://lab.dotjay.com/notes/voiceover-commands/)

## <a name="see-also"></a>Viz také

- [Funkce usnadnění v sadě Visual Studio (ve Windows)](/visualstudio/ide/reference/accessibility-features-of-visual-studio)