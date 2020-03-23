---
title: Použití definice náhledu
ms.date: 01/10/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9eac5c8c47c208f39f74f542fbbff89c8340a93f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591343"
---
# <a name="how-to-view-and-edit-code-by-using-peek-definition-altf12"></a>Postup: Zobrazení a úprava kódu pomocí definice náhledu (Alt+F12)

Příkaz Definice **náhledu** můžete použít k zobrazení a úpravám kódu, aniž byste museli přejít od kódu, který píšete. **Definice náhledu** a **Přejít na definici** zobrazují stejné informace, ale **definice náhledu** je zobrazuje v rozbalovacím okně a **přejít na definici** zobrazí kód v samostatném okně kódu. **Přejít na definici** způsobí, že váš kontext (to znamená aktivní okno kódu, aktuální řádek a pozice kurzoru) přepnout do okna kódu definice. Pomocí **definice náhledu**můžete zobrazit a upravit definici a pohybovat se uvnitř definičního souboru a přitom zachovat své místo v původním souboru kódu.

**Definici náhledu** můžete použít s kódem Jazyka C#, Visual Basic a C++. V jazyce Visual Basic **náhled definice** zobrazuje odkaz na **prohlížeč objektů** pro symboly, které nemají metadata definice (například typy .NET, které jsou integrovány).

## <a name="use-peek-definition"></a>Použití definice náhledu

### <a name="open-a-peek-definition-window"></a>Otevření okna Definice náhledu

1. Definici můžete nahlédnout tak, že z nabídky po kliknutí pravým tlačítkem myši vyberete **definici náhledu** pro typ nebo člena, který chcete prozkoumat. Pokud je tato možnost povolena, můžete také nahlédnout do definice pomocí myši stisknutím **klávesy Ctrl** (nebo jiného modifikátoru) a klepnutím na název člena. Nebo z klávesnice stiskněte **klávesu Alt**+**F12**.

     Tento obrázek znázorňuje okno **Definice náhledu** pro metodu s názvem `Print()`:

     ![Okno náhledu](../ide/media/peekwindow.png)

     Okno definice se `printer.Print("Hello World!")` zobrazí pod řádkem v původním souboru. Okno neskryje žádný kód v původním souboru. Následující řádky `printer.Print("Hello World!")` se zobrazí v okně definice.

1. Kurzor můžete přesunout na různá místa v okně definice náhledu. Můžete také stále pohybovat v původním okně kódu.

1. Můžete zkopírovat řetězec v okně definice a vložit ho do původního kódu. Můžete také přetáhnout řetězec z okna definice do původního kódu, aniž by byl v okně definice odstraněn.

1. Okno definice můžete zavřít výběrem klávesy **Esc** nebo tlačítka **Zavřít** na kartě okna definice.

### <a name="open-a-peek-definition-window-from-within-a-peek-definition-window"></a>Otevření okna Definice náhledu z okna Definice náhledu

Pokud již máte otevřené okno **Definice náhledu,** můžete znovu **zavolat definici náhledu** v kódu v tomto okně. Otevře se jiné okno definice. Vedle karty okna definice se zobrazí sada teček s popisem cesty, která slouží k navigaci mezi okny definice. Popisek tlačítka na každé tečce zobrazuje název souboru a cestu k souboru definice, který tečka přestavuje.

   ![Okno Náhledu v okně Náhled](../ide/media/peekwithinpeek.png)

### <a name="peek-definition-with-multiple-results"></a>Definice náhledu s více výsledky

Pokud použijete **Peek Definice** na kód, který má více než jednu definici (například částečnou třídu), seznam výsledků se zobrazí vpravo od zobrazení definice kódu. Můžete zvolit některý z výsledků v seznamu k zobrazení jeho definice.

   ![Okno náhledu z více výsledků](../ide/media/peekmultiple.png)

### <a name="edit-inside-the-peek-definition-window"></a>Úpravy v okně Definice náhledu

Když začnete upravovat v okně **Definice náhledu,** soubor, který upravujete, se automaticky otevře jako samostatná karta v editoru kódu a odráží provedené změny. V okně **Definice náhledu** můžete pokračovat v provádění, zpět a ukládání změn a karta bude tyto změny nadále odrážet. I když zavřete okno **Definice náhledu** bez uložení změn, můžete na kartě provést, vrátit zpět a uložit další změny a v okně **Definice náhledu** navázat přesně tam, kde jste skončili.

   ![Úpravy v okně náhledu](../ide/media/peekedit.png)

### <a name="to-change-options-for-peek-definition"></a>Změna možností definice náhledu

1. Přejděte na > Obecné textové > **editory** >  **možností nástrojů****.****Options**

1. Vyberte možnost **Otevřít definici v náhledovém zobrazení**.

1. Klepnutím na **tlačítko OK** zavřete dialogové okno **Možnosti.**

   ![Nastavení možnosti definice náhledu klepnutím myši](../ide/media/editor_options_peek_view.png)

### <a name="keyboard-shortcuts-for-peek-definition"></a>Klávesové zkratky pro definici náhledu

Tyto klávesové zkratky můžete použít v okně **Definice náhledu:**

|Funkce|Klávesová zkratka|
|-------------------|:-----------------------:|
|Otevřít okno definice|**Alt**+**F12**|
|Zavřít okno definice|**Esc**|
|Povýšit okno definice na běžnou kartu dokumentu|**Přesunout**+**alternativní domů**+**Home**|
|Navigace mezi okny definice|**Ctrl**+**Alt** + **-** Alt a **Ctrl**+**Alt**+**=**|
|Navigace mezi několika výsledky|**F8** a **posuňte**+**klávesu F8**|
|Přepnout mezi oknem editoru kódu a oknem definice|**Posun**+**esc**|

> [!NOTE]
> Můžete také použít stejné klávesové zkratky k úpravám kódu v okně **Definice náhledu** jako jinde v sadě Visual Studio.

## <a name="see-also"></a>Viz také

- [Navigace v kódu](../ide/navigating-code.md)
- [Přejít k definici a Náhled definice](../ide/go-to-and-peek-definition.md)
- [Funkce produktivity v sadě Visual Studio](../ide/productivity-features.md)
