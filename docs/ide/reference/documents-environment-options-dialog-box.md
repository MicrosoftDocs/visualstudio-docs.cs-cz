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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75570060"
---
# <a name="options-dialog-box-environment--documents"></a>Dialogové okno Možnosti: \> dokumenty prostředí

Pomocí této stránky dialogového okna **Možnosti** můžete řídit zobrazení dokumentů v integrovaném vývojovém prostředí (IDE) a spravovat externí změny dokumentů a souborů. K tomuto dialogovému oknu se dostanete tak, že v nabídce **nástroje** kliknete na **Možnosti** a pak vyberete **Environment**  >  **dokumenty**prostředí.

**Rozpoznat, kdy se soubor změnil mimo prostředí**

Pokud je vybrána tato možnost, zpráva okamžitě upozorní vás na změny otevřeného souboru, které byly provedeny editorem mimo rozhraní IDE. Tato zpráva umožňuje znovu načíst soubor z úložiště.

**Znovu načíst změněné soubory, pokud neexistují neuložené změny**

Když **zjistíte, že se soubor změnil mimo zvolené prostředí** a když se otevřený soubor v integrovaném vývojovém prostředí změní mimo IDE, ve výchozím nastavení se vygeneruje varovná zpráva. Pokud je tato možnost povolená, nezobrazí se žádné upozornění a dokument se znovu načte v integrovaném vývojovém prostředí, aby se vybraly externí změny.

**Povolí úpravy souborů jen pro čtení; Zobrazit upozornění při pokusu o uložení**

Když je tato možnost povolená, můžete otevřít a upravit soubor, který je jen pro čtení. Až budete hotovi, musíte použít příkaz **Uložit jako** a soubor uložit do nového názvu, pokud chcete uložit záznam změn.

**Otevřít soubor pomocí adresáře aktuálně aktivního dokumentu**

Pokud je tato možnost vybrána, tato možnost určuje, že dialogové okno **otevřít soubor** zobrazí adresář aktivního dokumentu. Pokud je tato možnost vymazána, zobrazí se dialogové okno **otevřít soubor** s adresářem naposledy použitým k otevření souboru.

**Při načtení kontrolovat konzistentní konce řádků**

Tuto možnost vyberte, pokud chcete, aby Editor kontroloval konce řádku v souboru a zobrazil okno se zprávou, pokud jsou zjištěny nekonzistence při formátování konců řádků.

**Zobrazit upozornění, pokud bude globální akce zpět upravovat upravované soubory**

Tuto možnost vyberte, pokud chcete zobrazit okno se zprávou, když bude **globální příkaz zpět** vracet refaktoring změn provedených v souborech, které se změnily i po operaci refaktoringu. Vrácení souboru do jeho stavu před refaktoringem může zahodit následné změny provedené v souboru.

**Zobrazit různé soubory v Průzkumník řešení**

Tuto možnost vyberte, pokud chcete zobrazit uzel **různé soubory** v **Průzkumník řešení**. Různé soubory jsou soubory, které nejsou přidružené k projektu nebo řešení, ale můžou se zobrazit v **Průzkumník řešení** pro vaše pohodlí.

> [!NOTE]
> Tuto možnost vyberte, pokud chcete povolit příkaz **Zobrazit v prohlížeči** v nabídce **soubor** pro webové dokumenty, které nejsou součástí aktivní webové aplikace.

**Položky uložené v projektu různých souborů**

Určuje počet souborů, které se mají zachovat, do složky **různé soubory** **Průzkumník řešení**. Tyto soubory jsou uvedeny i v případě, že již nejsou otevřeny v editoru. Můžete zadat libovolné celé číslo od 0 do 256. Výchozí hodnota je 0.

Například pokud nastavíte tuto možnost na 5 a máte otevřené 10 různých souborů, při zavření všech 10 souborů se ve složce **různé soubory** stále zobrazí prvních 5.

**Uložit dokumenty jako Unicode, pokud data nelze uložit ve znakové sadě**

Tuto možnost vyberte, pokud chcete, aby soubory obsahující informace nekompatibilní s vybranou znakovou stránkou byly ve výchozím nastavení uložené jako Unicode.

## <a name="see-also"></a>Viz také

- [Různé soubory](../../ide/reference/miscellaneous-files.md)
- [Hledání a nahrazení textu](../../ide/finding-and-replacing-text.md)
