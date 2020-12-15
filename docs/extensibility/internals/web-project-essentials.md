---
title: Základy webového projektu | Microsoft Docs
description: Přečtěte si o interních podrobnostech o fungování webových projektů v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1bf16582cdc9bba6529d237d74d56ebded299fb9
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487917"
---
# <a name="web-project-essentials"></a>Základy webového projektu
Webové projekty vytvářejí webové aplikace. Webový projekt můžete použít k vytvoření webové aplikace, která má inteligentní webové stránky. Inteligentní webová stránka obsahuje kód na straně serveru, který vykresluje webovou stránku na vyžádání.

 Pomocí tradičních programovacích jazyků, jako jsou [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] nebo [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] , můžete vytvořit inteligentní webové stránky, které budou shromažďovat a zpracovávat informace od uživatele, ukládat je do databáze a tak dále.

- Model kódu na pozadí přidruží závislé soubory zdrojového kódu k webovým stránkám, které mají příponu. aspx nebo. asmx. Hello. aspx může mít například závislé soubory zdrojového kódu hello.aspx.cs.

- Kód na straně serveru spojený s inteligentní webovou stránkou je zkompilován do spustitelného souboru, který je umístěn ve složce/Bin webu.

- Další soubory zdrojového kódu, jako jsou pomocné třídy, které nejsou přidruženy k určité webové stránce, jsou umístěny ve složce Web/App_Code.

  - Projekt webu (WSP) generuje jeden spustitelný soubor pro každou inteligentní webovou stránku. Další spustitelné soubory jsou vygenerovány ze všech souborů zdrojového kódu ve složce/App_Code.

  - Projekt webové aplikace (WAP) vytvoří jeden spustitelný soubor, který kombinuje kód pro všechny inteligentní webové stránky a všechny zdrojové soubory ve složce/App_Code.

- Soubor řešení pro webový projekt je umístěn odděleně od samotného webu. Ve výchozím nastavení se soubory řešení nacházejí v umístění \Documents and Settings \\ *YourAccount*\My Documents \\ *\<Visual Studio ####>* \Projects \\ *YourWebSite*.

  > [!NOTE]
  > Pokud chcete soubor řešení zachovat na webu, stačí ho jednoduše přesunout a znovu otevřít.

- Pokud otevřete web, který neobsahuje žádný soubor řešení v aplikaci Visual Studio, automaticky se vygeneruje nový soubor řešení.

- Webové projekty nemají žádné soubory projektu. Informace o projektu jsou uloženy v souboru řešení, v souboru web.config a jinde.

- Přidáním globálních vlastností do webového projektu se automaticky vytvoří soubor úložiště ve složce řešení webového projektu.

- Inteligentní webová stránka může být přidružena k programovacímu jazyku na straně serveru pomocí direktivy stránky nebo \<script runat="server"> značky.

- Kromě toho může mít webová stránka libovolný počet skriptovacích bloků na straně klienta napsaných v jakémkoli skriptovacím jazyce.

- Systém projektu webu je implementován přidáním šablon projektů a položek a registrací do [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] projektu.

- Systém WAP je implementován jako podtyp projektu, označovaný také jako charakter projektu. [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)]Projekt je určen podtypem WAP pro vytvoření systému WAP. Další informace o podtypůch projektů naleznete v tématu [podtypy projektu](../../extensibility/internals/project-subtypes.md).

- Inteligentní webová stránka kombinuje kód HTML s programovacím jazykem na straně serveru. Jazyk na straně serveru se nazývá obsažený jazyk. Pro podporu obsaženého jazyka musí systém webového projektu implementovat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> rodinu rozhraní.

  - Pro podporu obsažených jazyků v editoru musí služba jazyka HTML odložit zobrazení obsaženého kódu jazyka do obsažené jazykové služby.

  - Chybové značky (červené vlnovky) by se měly vždy vytvořit v primární vyrovnávací paměti editoru kódu.

## <a name="see-also"></a>Viz také
- [Webové projekty](../../extensibility/internals/web-projects.md)
