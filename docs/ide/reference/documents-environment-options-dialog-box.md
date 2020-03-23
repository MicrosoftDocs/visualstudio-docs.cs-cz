---
title: Dokumenty, prostředí, dialogové okno Možnosti
ms.date: 03/28/2019
ms.topic: reference
f1_keywords:
- VS.Environment.Documents
- VS.ToolsOptionsPages.Environment.Documents
helpviewer_keywords:
- Documents Environment Options dialog box
- defaults, directories
- error messages, customizing
- files [Visual Studio], default options
- files [Visual Basic], auto-loading modified
- windows, customizing environment
- in-memory editing
- folders [Visual Studio], specifying where Open File goes
- Open File dialog box
- windows, enabling re-use of current
- notifications, files changed
- files [Visual Studio], displaying in Solution Explorer
- default directories
- read-only files, editing
- Options dialog box, showing Miscellaneous Files
- directories [Visual Studio], IDE environment options
- Options dialog box, Documents page
- warnings, files changed
- Solution Explorer, displaying files in
ms.assetid: 4e3ccf1b-cd68-4db6-9470-710c911b47fc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7813a2e7686bef5a146e7472bce7f2c24baf9cd2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570060"
---
# <a name="options-dialog-box-environment--documents"></a>Dialogové okno Možnosti: Dokumenty prostředí \>

Na této stránce dialogového okna **Možnosti** můžete řídit zobrazení dokumentů v integrovaném vývojovém prostředí (IDE) a spravovat externí změny dokumentů a souborů. K tomuto dialogovému oknu se dostanete klepnutím na tlačítko **Možnosti** v nabídce **Nástroje** a výběrem**položky Dokumenty** **prostředí** > .

**Zjištění změny souboru mimo prostředí**

Je-li vybrána tato možnost, zpráva vás okamžitě upozorní na změny otevřeného souboru, které byly provedeny editorem mimo rozhraní IDE. Zpráva umožňuje znovu načíst soubor z úložiště.

**Opětovné načtení změněných souborů, pokud nejsou neuložené změny**

Pokud máte **zjistit, kdy je soubor změněn mimo** vybrané prostředí a otevřený soubor v ide změny mimo IDE, ve výchozím nastavení se vygeneruje varovná zpráva. Pokud je tato možnost povolena, nezobrazí se žádné upozornění a dokument se znovu načte v rozhraní IDE, aby se zachytily externí změny.

**Povolit úpravy souborů jen pro čtení; upozornit při pokusu o uložení**

Pokud je tato možnost povolena, můžete soubor jen pro čtení otevřít a upravit. Po dokončení je nutné použít příkaz **Uložit jako** k uložení souboru pod novým názvem, pokud chcete uložit záznam změn.

**Otevření souboru pomocí adresáře aktuálně aktivního dokumentu**

Když je tato volba vybraná, určuje, že v dialogovém okně **Otevřít soubor** se zobrazí adresář aktivního dokumentu. Pokud tato volba není zaškrtnuta, v dialogovém okně **Otevřít soubor** se zobrazí adresář, který naposledy otevřel soubor.

**Kontrola konzistentních zakončení čar při zatížení**

Tuto možnost vyberte, chcete-li, aby editor prohledává koncovky řádků v souboru a zobrazuje okno se zprávou, pokud jsou zjištěny nekonzistence ve způsobu formátování zakončení řádků.

**Zobrazit upozornění, když globální zrušení změny změní upravené soubory**

Tuto možnost vyberte, chcete-li zobrazit okno se zprávou, když příkaz **Globální zpět** vrátí zpět změny refaktoringu provedené v souborech, které byly také změněny po operaci refaktoringu. Vrácení souboru do stavu předběžnérefaktoring může zahodit následné změny provedené v souboru.

**Zobrazit různé soubory v Průzkumníku řešení**

Tuto možnost vyberte, chcete-li zobrazit uzel Různé **soubory** v **Průzkumníku řešení**. Různé soubory jsou soubory, které nejsou přidruženy k projektu nebo řešení, ale mohou se zobrazit v **Průzkumníku řešení** pro vaše pohodlí.

> [!NOTE]
> Tuto možnost vyberte, chcete-li povolit příkaz **Zobrazit v prohlížeči v** nabídce **Soubor** pro webové dokumenty, které nejsou zahrnuty v aktivní webové aplikaci.

**Položky uložené v projektu Různé soubory**

Určuje počet souborů, které mají být **uloženy** ve složce Různé soubory **průzkumníka řešení**. Tyto soubory jsou uvedeny i v případě, že již nejsou otevřeny v editoru. Můžete zadat libovolné celé číslo od 0 do 256. Výchozí číslo je 0.

Pokud například nastavíte tuto možnost na 5 a máte otevřeno 10 různých souborů, po zavření všech 10 souborů se prvních 5 stále zobrazí ve složce **Různé soubory.**

**Uložit dokumenty jako Unicode, když data nelze uložit do znakové stránky**

Tuto možnost vyberte, chcete-li, aby soubory obsahující informace nekompatibilní s vybranou znakovou stránkou byly ve výchozím nastavení uloženy jako Unicode.

## <a name="see-also"></a>Viz také

- [Různé soubory](../../ide/reference/miscellaneous-files.md)
- [Hledání a nahrazení textu](../../ide/finding-and-replacing-text.md)
