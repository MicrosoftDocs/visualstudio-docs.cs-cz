---
title: Tipy a triky pro usnadnění přístupu pro Visual Studio
description: Přečtěte si další informace o tipech a tricích, které můžou usnadnit integrované vývojové prostředí sady Visual Studio (IDE) pro všechny uživatele, včetně osob s postižením.
ms.date: 08/06/2019
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: 6b491d88-f79e-4686-8841-857624bdcfda
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5828fb114a4df559c46dd6ae7f64887ab48e7429
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "68919526"
---
# <a name="accessibility-tips-and-tricks-for-visual-studio"></a>Tipy a triky pro usnadnění přístupu pro Visual Studio

Visual Studio obsahuje integrované funkce usnadnění, které jsou kompatibilní s programy pro čtení z obrazovky a dalšími asistenčními technologiemi. Ať už chcete k navigaci v prostředí IDE používat klávesové zkratky nebo používat motivy s vysokým kontrastem ke zlepšení viditelnosti, najdete na této stránce několik tipů, & triky o tom, jak to udělat.

Také se zabýváme tím, jak pomocí poznámky odhalit užitečné informace o kódu a jak nastavit zvukové podněty pro sestavení a události zarážky.

> [!NOTE]
> Toto téma platí pro Visual Studio v systému Windows. Visual Studio pro Mac najdete [v tématu Usnadnění pro Visual Studio pro Mac](/visualstudio/mac/accessibility).

## <a name="save-your-ide-settings"></a>Uložení nastavení ide

Prostředí IDE můžete přizpůsobit uložením rozložení okna, schématu mapování klávesnice a dalších předvoleb. Další informace naleznete [v tématu Přizpůsobení prostředí IDE sady Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="modify-your-ide-for-high-contrast-viewing"></a>Úprava ide pro zobrazení s vysokým kontrastem

Pro některé lidi, některé barvy jsou obtížnější vidět. Pokud chcete větší kontrast, jak si kód, ale nechcete používat typické "Vysoký kontrast" témata, nyní nabízíme "Modrá (Extra Kontrast)" téma.

  ![Porovnání motivu Modrý a Modrý extra kontrast](media/blue-extra-contrast-theme.png "Snímek obrazovky, který zobrazuje porovnání modrého motivu a motivu Modrý extra kontrast")

## <a name="use-annotations-to-reveal-useful-information-about-your-code"></a>Použití poznámky odhalit užitečné informace o kódu

Editor sady Visual Studio obsahuje mnoho text "vylepšení", které vás upozorní na charakteristiky a funkce v určitých bodech na řádku kódu, jako je například šroubovák a žárovky ikony, chyby a varování "klikyháky", záložky a tak dále. Můžete použít sadu příkazů "Zobrazit anotace čar", která vám pomůže objevit a pak přejít mezi těmito vylepšeními.

  ![Použití sady příkazů Zobrazit poznámky z řádku](media/show-line-annotations-command-set.png "Snímek obrazovky s položkou nabídky Poznámky zobrazit řádek")

## <a name="access-toolbars-by-using-keyboard-shortcuts"></a>Přístup k panelům nástrojů pomocí klávesových zkratek

Prostředí IDE sady Visual Studio má panely nástrojů stejně jako mnoho oken nástrojů. K nim mají přístup následující klávesové zkratky.

|Funkce|Popis|Klávesová zkratka|
|-------------|-----------------| - |
|Panely nástrojů IDE|Vyberte první tlačítko na panelu nástrojů Standardní.|**Alt**,**karta** **Ctrl**+|
|Panely nástrojů okna nástrojů|Přesunutí fokusu na panely nástrojů v okně nástroje <br> <br> **POZNÁMKA:** To funguje pro většinu oken nástrojů, ale pouze v případě, že fokus je v okně nástroje. Musíte také před klávesou ALT zvolit klávesu SHIFT. V některých oknech nástrojů, například v Průzkumníkovi týmu, musíte před výběrem klávesy ALT chvíli podržet klávesu SHIFT.|**Posuntovat**+**s alternativním**|
|Panely nástrojů|Přejděte na první položku na dalším panelu nástrojů (pokud je zaostřeno na panelu nástrojů).|**Ctrl**+**Karta** Ctrl|

### <a name="other-useful-keyboard-shortcuts"></a>Další užitečné klávesové zkratky

Některé další užitečné klávesové zkratky zahrnují následující.

|Funkce|Popis|Klávesová zkratka|
|-------------|-----------------| - |
|IDE – integrované vývojové prostředí|Zapínejte a vypínejte vysoký kontrast. <br> <br> **POZNÁMKA:** Standardní klávesová zkratka pro Windows|**Levý alt**+**levý posun**+**PrtScn**|
|Dialogové okno|Zaškrtněte nebo zrušte zaškrtnutí políčka v dialogovém okně. <br> <br> **POZNÁMKA:** Standardní klávesová zkratka pro Windows|**Mezerník**|
|Místní nabídky|Otevřete kontextovou nabídku (po kliknutí pravým tlačítkem myši). <br> <br> **POZNÁMKA:** Standardní klávesová zkratka pro Windows|**Posun**+**F10**|
|Nabídky|Rychlý přístup k položce nabídky pomocí kláves akcelerátoru. Příkaz aktivujete zvolte klávesu **Alt** následovanou podtrženými písmeny v nabídce. Chcete-li například zobrazit dialogové okno Otevřít projekt v sadě Visual Studio, zvolíte možnost **Alt**+**F**+**O**+**P**.  <br><br> **POZNÁMKA:** Standardní klávesová zkratka pro Windows|**Alt** + **[dopis]**|
|Vyhledávací pole|Použijte funkci hledání v sadě Visual Studio.|**Ctrl**+**Q**|
|Okno panelu nástrojů|Přesun mezi kartami Panelu nástrojů|**Ctrl**+**šipka nahoru**<br /><br /> a<br /><br /> **Ctrl**+**šipka dolů**|
|Okno panelu nástrojů|Přidejte ovládací prvek z panelu nástrojů do formuláře nebo návrháře.|**Enter**|
|Dialogové okno Možnosti: Prostředí > klávesnice|Odstraňte kombinaci kláves zadanou v možnosti **Natisknout klávesové zkratky.**|**Backspace**|
|Okno nástroje Oznámení|Otevřete okno nástroje Oznámení pomocí dvou kombinací klávesových zkratek, jedné následované druhou. Potom zobrazte oznámení pomocí kláves se šipkami a vyberte ho.| **Ctrl** + **&#92;**, **Ctrl**+**N**|

> [!NOTE]
> Zobrazená dialogová okna a příkazy nabídek se mohou lišit od těch, které jsou popsány v nápovědě, v závislosti na aktivním nastavení nebo edici.

## <a name="access-notifications-by-using-keyboard-shortcuts"></a>Přístup k oznámením pomocí klávesových zkratek

Když se v ide zobrazí oznámení, můžete získat přístup k oknu Oznámení pomocí klávesových zkratek:

1. Z libovolného místa v ide, stiskněte následující dvě klávesové zkratky v pořadí, jeden po druhém: **Ctrl** + **&#92;** a pak **Ctrl**+**N**.

   Otevře se okno **Oznámení.**

   ![Okno nástroje Oznámení v ide sady Visual Studio](media/toast-notification.png "Snímek obrazovky s oknem Oznámení v rozhraní IDE sady Visual Studio")

1. Pomocí klávesy **Tab** nebo kláves se šipkami vyberte oznámení.

## <a name="use-the-sound-applet-to-set-build-and-breakpoint-cues"></a>Použití apletu Zvuku k nastavení podnětů sestavení a zarážky

Aplet zvuku v systému Windows můžete použít k přiřazení zvuku k událostem programu sady Visual Studio. Konkrétně můžete přiřadit zvuky k následujícím událostem programu:

* Zásahová stopa
* Sestavení bylo zrušeno.
* Sestavení se nezdařilo.
* Sestavení proběhlo úspěšně.

Zde je uveden postup:

1. Do pole **Hledat** v počítači se systémem Windows 10 zadejte **příkaz Změnit systémové zvuky**.

   ![Vyhledávací pole ve Windows 10](media/type-here-to-search.png "Snímek obrazovky s vyhledávacím polem ve Windows 10")

   (Pokud máte cortanu povolenou, řekněte "Hey Cortana" a pak řekněte "Změnit systémové zvuky".)

1. Poklepejte na **změnit systémové zvuky**.

   ![Výsledky hledání ve Windows 10](media/change-system-sounds.png "Snímek obrazovky s výsledky hledání "Změnit zvuky systému" ve Windows 10")

1. V dialogovém okně **Zvuk** klikněte na kartu **Zvuky.**

1. V **části Události programů**přejděte na **aplikaci Microsoft Visual Studio**a vyberte zvuky, které chcete použít pro vybrané události.

   ![Zvuková karta apletu Zvuk ve Windows 10](media/sound-applet.png "Zvuková karta apletu Zvuk ve Windows 10")

1. Klikněte na tlačítko **OK**.

::: moniker range="vs-2017"

> [!TIP]
> Další informace o aktualizacích usnadnění najdete v tématu Vylepšení usnadnění v blogu [Visual Studia 2017 verze 15.3.](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/)

::: moniker-end

## <a name="see-also"></a>Viz také

* [Funkce usnadnění v sadě Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Postup: Přizpůsobení nabídek a panelů nástrojů v sadě Visual Studio](../../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
* [Přizpůsobení prostředí IDE sady Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
* [Usnadnění přístupu (Visual Studio pro Mac)](/visualstudio/mac/accessibility)
* [Usnadnění přístupu společnosti Microsoft](https://www.microsoft.com/Accessibility)
