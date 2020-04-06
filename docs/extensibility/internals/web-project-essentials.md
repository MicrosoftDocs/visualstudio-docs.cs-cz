---
title: Základy webového projektu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09e33248ca264fefa79a8d5d5fa5d0cfa3d2da1d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703541"
---
# <a name="web-project-essentials"></a>Základy webového projektu
Webové projekty vytvářejí webové aplikace. Webový projekt můžete použít k vytvoření webové aplikace s inteligentními webovými stránkami. Inteligentní webová stránka obsahuje kód na straně serveru, který vykresluje webovou stránku na vyžádání.

 Pomocí tradičních programovacích [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]jazyků, například nebo , můžete vytvářet inteligentní webové stránky pro shromažďování a zpracování informací od uživatele, jejich ukládání do databáze a tak dále.

- Model s kódem na pozadí přidruží závislé soubory zdrojového kódu k webovým stránkám, které mají příponu aspx nebo asmx. Například hello.aspx může mít hello.aspx.cs závislý soubor zdrojového kódu.

- Kód na straně serveru přidružený k inteligentní webové stránce je zkompilován do spustitelného souboru umístěného ve složce web /bin.

- Další soubory zdrojového kódu, například pomocné třídy, které nejsou přidruženy k určité webové stránce, jsou umístěny ve složce web /App_Code.

  - Webový projekt (WSP) generuje jeden spustitelný soubor pro každou inteligentní webovou stránku. Další spustitelné soubory jsou generovány ze všech souborů zdrojového kódu ve složce /App_Code.

  - Projekt webové aplikace (WAP) vytvoří jeden spustitelný soubor, který kombinuje kód pro všechny inteligentní webové stránky, stejně jako všechny zdrojové soubory ve složce /App_Code.

- Soubor řešení pro webový projekt je umístěn odděleně od samotného webu. Ve výchozím nastavení jsou soubory řešení\\umístěny na adrese \Documents and Settings\\*YourAccount*\My Documents\\*\<Visual Studio ####>* \Projects*YourWebSite*.

  > [!NOTE]
  > Pokud chcete zachovat soubor řešení s webem, stačí jej přesunout tam a znovu jej otevřít.

- Pokud otevřete web, který nemá žádný soubor řešení v sadě Visual Studio, bude pro něj automaticky vygenerován nový soubor řešení.

- Webové projekty nemají žádné soubory projektu. Informace o projektu jsou uloženy v souboru řešení, souboru web.config a jinde.

- Přidání matných vlastností do webového projektu automaticky vytvoří soubor úložiště ve složce řešení webového projektu.

- Inteligentní webová stránka může být přidružena k programovacímu jazyku na straně serveru pomocí směrnice Page nebo značky > skriptrunat="server". \<

- Kromě toho webové stránky mohou mít libovolný počet bloků skriptování na straně klienta napsaných v libovolném skriptovacím jazyce.

- Systém projektu webu je implementován přidáním šablon projektů [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] a položek a registrací do projektu.

- Systém WAP je implementován jako podtyp projektu, nazývaný také příchuť projektu. Projekt [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] je ochucený podtypem WAP k vytvoření systému WAP. Další informace o podtypech projektů naleznete v [tématu Podtypy projektu](../../extensibility/internals/project-subtypes.md).

- Inteligentní webová stránka kombinuje html s programovacím jazykem na straně serveru. Jazyk na straně serveru se nazývá obsažený jazyk. Pro podporu obsaženého jazyka musí systém webových projektů implementovat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> rodinu rozhraní.

  - Pro podporu obsaženého jazyka v editoru musí jazyková služba HTML odložit zobrazení obsaženého kódu jazyka na službu obsahující jazyk.

  - Značky chyb (červené klikyháky) by měly být vždy vytvořeny v primární vyrovnávací paměti editoru kódu.

## <a name="see-also"></a>Viz také
- [Webové projekty](../../extensibility/internals/web-projects.md)
