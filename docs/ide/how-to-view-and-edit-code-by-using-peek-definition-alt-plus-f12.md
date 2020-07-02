---
title: Použití náhledu definice
ms.date: 01/10/2018
ms.topic: how-to
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: daa1148a47919c12fa423bd90f6d63c030cf743c
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770525"
---
# <a name="how-to-view-and-edit-code-by-using-peek-definition-altf12"></a>Postupy: zobrazení a úpravy kódu pomocí funkce Náhled definice (Alt + F12)

Pomocí příkazu **Náhled definice** můžete zobrazit a upravit kód bez přepínání mimo kód, který píšete. **Náhled definice** a **Přejít k definici** zobrazí stejné informace, ale **Náhled definice** je zobrazí v místním okně a **Přejít k definici** zobrazuje kód v samostatném okně kódu. **Přejít k definici** způsobí, že váš kontext (tj. aktivní okno kódu, aktuální řádek a pozice kurzoru) přepne do okna kód definice. Pomocí **náhledu definice**můžete zobrazit a upravit definici a přesunout se v rámci souboru definice a přitom zachovat místo v původním souboru kódu.

Můžete použít **Náhled definice** s kódem C#, Visual Basic a C++. V Visual Basic **Náhled definice** zobrazuje odkaz na **Prohlížeč objektů** pro symboly, které nemají Metadata definice (například typy .NET, které jsou integrovány).

## <a name="use-peek-definition"></a>Použít náhled definice

### <a name="open-a-peek-definition-window"></a>Otevření okna Náhled definice

1. Definici můžete prohlížet výběrem možnosti **Náhled definice** v nabídce kliknutím pravým tlačítkem pro typ nebo člen, který chcete prozkoumat. Pokud je tato možnost povolená, můžete také pomocí myši pomocí **klávesy CTRL** (nebo jiného modifikátoru) prohlížet definice a kliknout na název člena. Nebo na klávesnici stiskněte klávesu **ALT** + **F12**.

     Tento obrázek ukazuje okno **Náhled definice** pro metodu s názvem `Print()` :

     ![Náhled okna](../ide/media/peekwindow.png)

     Okno definice se zobrazí pod `printer.Print("Hello World!")` řádkem v původním souboru. Okno neskryje žádný kód v původním souboru. Řádky, které následují, `printer.Print("Hello World!")` se zobrazí pod oknem definice.

1. Kurzor můžete přesunout do různých míst v okně Náhled definice. Můžete se také dál pohybovat v původním okně kódu.

1. Můžete zkopírovat řetězec v okně definice a vložit ho do původního kódu. Můžete také přetáhnout řetězec z okna definice do původního kódu, aniž by byl v okně definice odstraněn.

1. Okno definice můžete zavřít kliknutím na klávesu **ESC** nebo tlačítkem **Zavřít** na kartě okno definice.

### <a name="open-a-peek-definition-window-from-within-a-peek-definition-window"></a>Otevření okna Náhled definice v okně Náhled definice

Pokud již máte otevřené okno **Náhled definice** , můžete znovu zavolat **Náhled definice** na kód v tomto okně. Otevře se jiné okno definice. Vedle karty okna definice se zobrazí sada teček s popisem cesty, která slouží k navigaci mezi okny definice. Popisek tlačítka na každé tečce zobrazuje název souboru a cestu k souboru definice, který tečka přestavuje.

   ![Náhled okna v náhledu](../ide/media/peekwithinpeek.png)

### <a name="peek-definition-with-multiple-results"></a>Náhled definice s více výsledky

Použijete-li **Náhled definice** v kódu, který má více než jednu definici (například částečné třídy), seznam výsledků se zobrazí napravo od zobrazení definice kódu. Můžete zvolit některý z výsledků v seznamu k zobrazení jeho definice.

   ![Náhled okna z více výsledků](../ide/media/peekmultiple.png)

### <a name="edit-inside-the-peek-definition-window"></a>Upravit v okně Náhled definice

Když začnete upravovat v okně **Náhled definice** , soubor, který upravujete, se automaticky otevře jako samostatná karta v editoru kódu a projeví se změny, které jste udělali. V okně **Náhled definice** můžete dál dělat, vracet a ukládat změny a karta bude tyto změny dál zobrazovat. I když zavřete okno **Náhled definice** bez uložení změn, můžete na kartě dělat, vracet a ukládat další změny, a to přesně tam, kde jste skončili v okně **Náhled definice** .

   ![Úpravy v náhledu okna](../ide/media/peekedit.png)

### <a name="to-change-options-for-peek-definition"></a>Změna možností pro náhled definice

1. V **nabídce nástroje**  >  **Možnosti**  >  **textový editor**  >  **Obecné**.

1. **V zobrazení Náhled vyberte možnost otevřená definice**.

1. Kliknutím na tlačítko **OK** zavřete dialogové okno **Možnosti** .

   ![Nastavení možnosti Náhled definice v nabídce myši](../ide/media/editor_options_peek_view.png)

### <a name="keyboard-shortcuts-for-peek-definition"></a>Klávesové zkratky pro náhled definice

Tyto klávesové zkratky můžete použít v okně **Náhled definice** :

|Funkce|Klávesová zkratka|
|-------------------|:-----------------------:|
|Otevřít okno definice|**ALT** + **F12**|
|Zavřít okno definice|**Esc**|
|Povýšit okno definice na běžnou kartu dokumentu|**Posun** + **ALT** + **Domovská stránka**|
|Navigace mezi okny definice|**CTRL** + **Alt** + ALT **-** a **CTRL** + **+ ALT**+**=**|
|Navigace mezi několika výsledky|**F8** a **SHIFT** + **F8**|
|Přepnout mezi oknem editoru kódu a oknem definice|**Posun** + **Klávesa ESC**|

> [!NOTE]
> Můžete také použít stejné klávesové zkratky pro úpravu kódu v okně **Náhled definice** při použití jinde v aplikaci Visual Studio.

## <a name="see-also"></a>Viz také:

- [Navigace v kódu](../ide/navigating-code.md)
- [Přejít k definici a Náhled definice](../ide/go-to-and-peek-definition.md)
- [Funkce pro produktivitu v aplikaci Visual Studio](../ide/productivity-features.md)
