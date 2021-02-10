---
title: Tipy a triky pro usnadnění pro Visual Studio
description: Přečtěte si další informace o tipech a štychech, které vám pomůžou usnadnit přístup k integrovanému vývojovému prostředí (IDE) sady Visual Studio pro všechny uživatele, včetně postižených uživatelů.
ms.date: 08/06/2019
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: 6b491d88-f79e-4686-8841-857624bdcfda
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 59206c206f04aaf3506771ee2310daebd0af273a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939744"
---
# <a name="accessibility-tips-and-tricks-for-visual-studio"></a>Tipy a triky pro usnadnění pro Visual Studio

Visual Studio obsahuje integrované funkce pro usnadnění přístupu, které jsou kompatibilní s čtečkami obrazovky a dalšími technologiemi usnadnění. Bez ohledu na to, jestli chcete používat klávesové zkratky k procházení IDE nebo k lepší viditelnosti použít kvalitní motivy, najdete na této stránce několik & tipů, jak to udělat.

Také pokryjeme, jak používat poznámky k odhalení užitečných informací o vašem kódu a jak nastavit zvukové pomůcky pro události sestavení a zarážky.

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac najdete v tématu [přístupnost pro Visual Studio pro Mac](/visualstudio/mac/accessibility).

## <a name="save-your-ide-settings"></a>Uložení nastavení IDE

Prostředí IDE můžete přizpůsobit uložením rozložení okna, schématu mapování klávesnice a dalších předvoleb. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="modify-your-ide-for-high-contrast-viewing"></a>Úprava prostředí IDE pro zobrazení s vysokým kontrastem

U některých lidé se některé barvy obtížně zobrazují. Pokud chcete při kódování větší kontrast, ale nechcete používat typické motivy "Vysoký kontrast", teď nabízíme motiv "modrý (extra Contrast)".

  ![Porovnat modrý motiv a modrý motiv extra Contrast](media/blue-extra-contrast-theme.png "Snímek obrazovky znázorňující porovnání modrého motivu a modrého motivu s modrým kontrastem")

## <a name="use-annotations-to-reveal-useful-information-about-your-code"></a>Použití poznámek k odhalení užitečných informací o kódu

Editor sady Visual Studio obsahuje mnoho textových "vylepšení", která vám pomůžou zjistit charakteristiky a funkce na určitých místech na řádku kódu, jako jsou ikony Screwdriver a žárovky, chyby a varování "vlnovky", záložky atd. Můžete použít sadu příkazů zobrazit poznámky k řádkům, které vám pomohou zjistit a procházet mezi těmito doplňky.

  ![Použití sady příkazů zobrazit poznámky k řádkům](media/show-line-annotations-command-set.png "Snímek obrazovky s položkou nabídky Zobrazit poznámky k řádkům")

## <a name="access-toolbars-by-using-keyboard-shortcuts"></a>Přístup k panelům nástrojů pomocí klávesových zkratek

Integrované vývojové prostředí sady Visual Studio má panely nástrojů jako mnoho oken nástrojů. Následující klávesové zkratky vám pomůžou s přístupem k nim.

|Funkce|Popis|Klávesová zkratka|
|-------------|-----------------| - |
|Panely nástrojů IDE|Vyberte první tlačítko na standardním panelu nástrojů.|**ALT**,  + **TAB** CTRL|
|Panely nástrojů okna nástrojů|Přesuňte fokus na panely nástrojů v okně nástroje. <br> <br> **Poznámka:** Tato funkce funguje pro většinu oken nástrojů, ale pouze v případě, že je fokus v okně nástroje. Také je nutné před klávesou ALT zvolit klávesu SHIFT. V některých oknech nástrojů, jako je například Team Explorer, je nutné před volbou klávesy ALT držet chvilku klávesu SHIFT.|**Posun** + **ALT**|
|Panely nástrojů|Přejít na první položku na následujícím panelu nástrojů (Pokud má panel nástrojů fokus).|**CTRL** + **Karta**|

### <a name="other-useful-keyboard-shortcuts"></a>Další užitečné klávesové zkratky

Mezi další užitečné klávesové zkratky patří následující.

|Funkce|Popis|Klávesová zkratka|
|-------------|-----------------| - |
|IDE – integrované vývojové prostředí|Přepnutí Vysoký kontrast zapnuto nebo vypnuto. <br> <br> **Poznámka:** Standardní klávesové zkratky Windows|**Levá klávesa ALT** + **Posun doleva** + **Print Screen**|
|Dialogové okno|Zaškrtněte nebo zrušte zaškrtnutí možnosti zaškrtávací políčko v dialogovém okně. <br> <br> **Poznámka:** Standardní klávesové zkratky Windows|**Mezerník**|
|Místní nabídky|Otevřete místní nabídku (kliknutím pravým tlačítkem myši). <br> <br> **Poznámka:** Standardní klávesové zkratky Windows|**Posun** + **F10**|
|Nabídky|Rychlý přístup k položce nabídky pomocí jeho klávesových zkratek Příkaz aktivujete tak, že v nabídce vyberete klávesu **ALT** následovanou podtrženými písmeny. Například pro zobrazení dialogového okna otevřít projekt v aplikaci Visual Studio byste si zvolili **ALT** + **F** + **O** + **P**.  <br><br> **Poznámka:** Standardní klávesové zkratky Windows|**ALT**  +  **[Letter]**|
|Vyhledávací pole|Použijte funkci hledání v aplikaci Visual Studio.|**CTRL** + **Otázka**|
|Okno panelu nástrojů|Přesun mezi kartami sady nástrojů|**CTRL** + **Šipka nahoru**<br /><br /> a<br /><br /> **CTRL** + **Šipka dolů**|
|Okno panelu nástrojů|Přidejte ovládací prvek ze sady nástrojů do formuláře nebo návrháře.|**Enter**|
|Dialogové okno Možnosti: prostředí > klávesnice|Odstraní kombinaci kláves zadaná v možnosti klávesových **zkratek** CTRL.|**Backspace**|
|Okno nástroje oznámení|Otevřete okno nástroje oznámení pomocí dvou kombinací kláves klávesových zkratek, jednu následovaný druhým. Potom zobrazte oznámení pomocí kláves se šipkami a vyberte je.| **CTRL** + **&#92;**, **CTRL** + **N**|

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.

## <a name="access-notifications-by-using-keyboard-shortcuts"></a>Přístup k oznámením pomocí klávesových zkratek

Když se v integrovaném vývojovém prostředí zobrazí oznámení, můžete získat přístup k oknu oznámení pomocí klávesových zkratek:

1. Z libovolného místa v integrovaném vývojovém prostředí (IDE) stiskněte následující dvě klávesové zkratky v sekvenci, jednu po druhé: **CTRL** + **&#92;** a pak **CTRL** + **N**.

   Otevře se okno **oznámení** .

   ![Okno nástroje oznámení v integrovaném vývojovém prostředí sady Visual Studio](media/toast-notification.png "Snímek obrazovky okna oznámení v integrovaném vývojovém prostředí sady Visual Studio")

1. K výběru oznámení použijte klávesu **TAB** nebo klávesy se šipkami.

## <a name="use-the-sound-applet-to-set-build-and-breakpoint-cues"></a>Použití apletu zvuk k nastavení hromádek sestavení a zarážky

Pomocí apletu zvuk v systému Windows můžete přiřadit zvuk k událostem programu Visual Studio. Konkrétně můžete přiřadit zvuky k následujícím událostem programu:

* Pozice zarážky
* Sestavení bylo zrušeno
* Sestavení selhalo
* Sestavení bylo úspěšné.

Jak na to:

1. Do **vyhledávacího** pole na počítači s Windows 10 zadejte **změnit systémové zvuky**.

   ![Vyhledávací pole ve Windows 10](media/type-here-to-search.png "Snímek obrazovky vyhledávacího pole ve Windows 10")

   (Případně, pokud máte Cortana povoleno, řekněme "Hey Cortana" a pak vyslovte "změnit systémové zvuky".)

1. Dvakrát klikněte na možnost **změnit systémové zvuky**.

   ![Výsledky hledání ve Windows 10](media/change-system-sounds.png "Snímek obrazovky s výsledky hledání "Změna systémových zvuků" ve Windows 10")

1. V dialogovém okně **zvuk** klikněte na kartu **zvuky** .

1. V okně **události programu** přejděte na **Microsoft Visual Studio** a pak vyberte zvuky, které chcete použít pro vybrané události.

   ![Karta zvuky v apletu zvuk v systému Windows 10](media/sound-applet.png "Karta zvuky v apletu zvuk v systému Windows 10")

1. Klikněte na **OK**.

::: moniker range="vs-2017"

> [!TIP]
> Další informace o aktualizacích usnadnění najdete v blogovém příspěvku o [vylepšeních dostupnosti v aplikaci Visual Studio 2017 verze 15,3](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) .

::: moniker-end

## <a name="see-also"></a>Viz také

* [Funkce usnadnění v aplikaci Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Postupy: přizpůsobení nabídek a panelů nástrojů v aplikaci Visual Studio](../../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
* [Přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
* [Usnadnění (Visual Studio pro Mac)](/visualstudio/mac/accessibility)
* [Usnadnění Microsoftu](https://www.microsoft.com/Accessibility)
