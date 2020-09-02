---
title: Dokumenty, prostředí, dialogové okno Možnosti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.Environment.Documents
- VS.ToolsOptionsPages.Environment.Documents
- VS.ToolsOptionsPag.Environment.Documents
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
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 705b1a5992d1a3e7931c316c713d46e7e8c7f72e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657774"
---
# <a name="documents-environment-options-dialog-box"></a>Dokumenty, prostředí, dialogové okno Možnosti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pomocí této stránky dialogového okna **Možnosti** můžete řídit zobrazení dokumentů v integrovaném vývojovém prostředí (IDE) a spravovat externí změny dokumentů a souborů. K tomuto dialogovému oknu se dostanete tak, že v nabídce **nástroje** kliknete na **Možnosti** a pak vyberete **dokumenty** v uzlu **prostředí** . Pokud se v seznamu nezobrazí **dokumenty** , vyberte v dialogovém okně **Možnosti** možnost **Zobrazit všechna nastavení** .

> [!NOTE]
> Možnosti dostupné v dialogových oknech a názvy a umístění příkazů nabídky, které vidíte, se mohou lišit od toho, co je popsáno v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 **Znovu použít aktuální okno dokumentu, pokud je uloženo** Když je tato možnost vybrána, zavře aktuální dokument, pokud byl uložen, a otevře nový dokument ve stejném okně. Pokud váš aktuální dokument není uložený, zůstane otevřený a nový dokument se otevře v samostatném okně. Pokud je tato možnost prázdná, nové dokumenty se vždy otevřou v samostatných oknech.

 Pokud provádíte operace vyjímání a vkládání více dokumentů zřídka a chcete minimalizovat počet otevřených dokumentů a oken v pracovním prostoru, zkuste tuto možnost.

 **Rozpoznat, kdy se soubor změnil mimo prostředí** Pokud je vybrána tato možnost, zpráva okamžitě upozorní vás na změny otevřeného souboru, které byly provedeny editorem mimo rozhraní IDE. Tato zpráva umožňuje znovu načíst soubor z úložiště.

 **Automaticky načíst změny, pokud jsou uloženy** Když **zjistíte, že se soubor změnil mimo zvolené prostředí** a když se otevřený soubor v integrovaném vývojovém prostředí změní mimo IDE, ve výchozím nastavení se vygeneruje varovná zpráva. Pokud je tato možnost povolená, nezobrazí se žádné upozornění a dokument se znovu načte v integrovaném vývojovém prostředí, aby se vybraly externí změny.

 **Povoluje úpravy souborů jen pro čtení; upozorňovat při pokusu o uložení** Pokud je tato možnost povolena, můžete otevřít a upravit soubor, který je jen pro čtení. Až budete hotovi, musíte použít příkaz **Uložit jako**a soubor uložit do nového názvu, pokud chcete uložit záznam změn.

 **Otevřít soubor pomocí adresáře aktuálně aktivního dokumentu** Pokud je tato možnost vybrána, tato možnost určuje, že dialogové okno **otevřít soubor** zobrazí adresář aktivního dokumentu. Pokud je tato možnost vymazána, zobrazí se dialogové okno **otevřít soubor** s adresářem naposledy použitým k otevření souboru.

 Při **načtení kontrolovat konzistentní konce řádků** Tuto možnost vyberte, pokud chcete, aby Editor kontroloval konce řádku v souboru a zobrazil okno se zprávou, pokud jsou zjištěny nekonzistence při formátování konců řádků.

 **Zobrazit upozornění, pokud bude globální akce zpět upravovat upravované soubory** Tuto možnost vyberte, pokud chcete zobrazit okno se zprávou, když bude **globální příkaz zpět** vracet refaktoring změn provedených v souborech, které se změnily i po operaci refaktoringu. Vrácení souboru do jeho stavu před refaktoringem může zahodit následné změny provedené v souboru.

 **Zobrazit různé soubory v Průzkumník řešení** Tuto možnost vyberte, pokud chcete zobrazit uzel **různé soubory** v **Průzkumník řešení**. Různé soubory jsou soubory, které nejsou přidružené k projektu nebo řešení, ale můžou se zobrazit v **Průzkumník řešení** pro vaše pohodlí.

> [!NOTE]
> Tuto možnost vyberte, pokud chcete povolit příkaz **Zobrazit v prohlížeči** v nabídce **soubor** pro webové dokumenty, které nejsou součástí aktivní webové aplikace.

 ** \<** *n* **> položky uložené v projektu různé soubory** určují počet souborů, které mají být uchovány ve složce **MiscellaneousFiles** **Průzkumník řešení**. Tyto soubory jsou uvedeny i v případě, že již nejsou otevřeny v editoru. Můžete zadat libovolné celé číslo od 0 do 256. Výchozí hodnota je 0.

 Například pokud nastavíte tuto možnost na 5 a máte otevřené 10 různých souborů, při zavření všech 10 souborů se ve složce **různé soubory** stále zobrazí prvních 5.

 **Uložit dokumenty jako Unicode, pokud data nelze uložit ve znakové sadě** Tuto možnost vyberte, pokud chcete, aby soubory obsahující informace nekompatibilní s vybranou znakovou stránkou byly ve výchozím nastavení uložené jako Unicode.

## <a name="see-also"></a>Viz také
 [Dialogové okno Možnosti prostředí](../../ide/reference/environment-options-dialog-box.md) [různé soubory](../../ide/reference/miscellaneous-files.md) [hledání a nahrazování textu](../../ide/finding-and-replacing-text.md)
