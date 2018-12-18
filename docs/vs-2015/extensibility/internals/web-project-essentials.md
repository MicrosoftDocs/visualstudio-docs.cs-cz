---
title: Web Essentials projektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6343860465cc5c8acdefb80a39eac3c33087a36d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51748851"
---
# <a name="web-project-essentials"></a>Základy webového projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Webové projekty vytvářet webové aplikace. Webový projekt můžete použít k vytvoření webové aplikace, která obsahuje inteligentní webové stránky. Inteligentní webová stránka obsahuje kód na straně serveru, který vykreslí webovou stránku na vyžádání.  
  
 Pomocí tradičních programovacích jazycích, jako například [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../includes/csprcs-md.md)], můžete vytvářet inteligentní webové stránky ke shromažďování a zpracování informací od uživatele, ukládat v databázi a tak dále.  
  
-   Model použití modelu code-behind přidruží webové stránky, které mají soubor .aspx rozšíření nebo ASMX závislé zdrojové soubory. Například hello.aspx pravděpodobně hello.aspx.cs závislé zdrojový kód souboru.  
  
-   Kód na straně serveru související s inteligentní webové stránky je zkompilován do spustitelného souboru, který je umístěný ve složce/Bin webové stránky.  
  
-   Soubory další zdrojového kódu, jako je například tříd pomocných rutin, které nejsou spojeny s konkrétní webovou stránku, jsou umístěny ve složce /App_Code webu.  
  
    -   Projekt webu (soubor WSP) generuje jeden spustitelný soubor pro každé inteligentní webové stránky. Další spustitelné soubory jsou generovány z jakékoli soubory zdrojového kódu ve složce /App_Code.  
  
    -   Projekt webové aplikace (WAP) vytvoří jeden spustitelný soubor, který kombinuje kód pro všechny inteligentní webové stránky, jakož i všechny zdrojové soubory ve složce /App_Code.  
  
-   Soubor řešení pro webový projekt nachází odděleně od samotného webového serveru. Ve výchozím nastavení, řešení soubory jsou umístěny v \Documents and nastavení\\*Váš_účet*\My dokumenty\\*\<sady Visual Studio ### >* \Projects\\ *YourWebSite*.  
  
    > [!NOTE]
    >  Pokud chcete zachovat soubor řešení s webovým serverem, stačí přesuňte ho tam a znovu ho otevřete.  
  
-   Pokud otevřete web, který nemá žádný soubor řešení v sadě Visual Studio nový soubor řešení není automaticky vygenerován pro něj.  
  
-   Webové projekty mít žádné soubory projektu. Informace o projektu je uložen v souboru řešení, v souboru web.config a jinde.  
  
-   Přidání globálních vlastností do webového projektu automaticky vytvoří soubor úložiště ve složce webového projektu řešení.  
  
-   Inteligentní webové stránky můžou být spojené s programovací jazyk na straně serveru pomocí direktivě stránky nebo \<skriptu runat = "server" > značky.  
  
-   Kromě toho webové stránky můžete mít libovolný počet bloků skriptování na straně klienta napsané v libovolném jazyce skriptování.  
  
-   Systém projektu webu je implementováno přidávání šablon projektů a položek a registraci [!INCLUDE[vwprvw](../../includes/vwprvw-md.md)] projektu.  
  
-   Systém WAP se implementuje jako podtyp projektu, také nazývané charakterem projektu. [!INCLUDE[vwprvw](../../includes/vwprvw-md.md)] Projektu je flavored podle podtyp WAP k vytvoření systému WAP. Další informace o podtypů projektů, naleznete v tématu [podtypů projektů](../../extensibility/internals/project-subtypes.md).  
  
-   Inteligentní webové stránky kombinuje HTML s programovací jazyk na straně serveru. Jazyk na straně serveru se nazývá omezením jazyka. Pro podporu omezením jazyka, musí implementovat systém webového projektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> řady rozhraní.  
  
    -   Pro podporu jazyka obsažené v editoru, musíte odložit služba jazyka HTML zobrazení kódu s omezením jazyka službě omezením jazyka.  
  
    -   Označování chyb (červená squigglies) by měl vždycky vytvořit v primární vyrovnávací paměť editoru kódu.  
  
## <a name="see-also"></a>Viz také  
 [Webové projekty](../../extensibility/internals/web-projects.md)

