---
title: Zdroj rozhodnutí o návrhu řízení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b0385d5feb7baf7fe60e253616c8db0f326932e9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131311"
---
# <a name="source-control-design-decisions"></a>Rozhodnutí o návrhu zdroj ovládacího prvku
Následující rozhodnutí o návrhu měli zvážit pro projekty při implementaci správy zdrojového kódu.  
  
## <a name="will-information-be-shared-or-private"></a>Bude informace sdílené nebo privátní?  
 Nejdůležitější rozhodnutí o návrhu, které lze provést je informací lze sdílet a co je soukromé. Například se sdílí ze seznamu souborů projektu, ale v rámci tento seznam souborů, někteří uživatelé měli mít privátní soubory. Kompilátor – nastavení jsou sdíleny, ale je obecně privátní spuštění projektu. Nastavení jsou čistě sdílené, sdílené s přepsání nebo čistě privátní. Návrh privátní položek, například uživatele řešení možnosti soubory (.suo), nejsou zaškrtnutí do [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]. Uložte nějaké soukromé informace v soukromé soubory, jako je například .suo soubor nebo soubor konkrétní privátní vytvoříte, například. csproj.user souboru pro Visual C# nebo. vbproj.user souboru v jazyce Visual Basic.  
  
 Toto rozhodnutí není kompletní a může být vytvořen na základě jednotlivých položek.  
  
## <a name="will-the-project-include-special-files"></a>Zahrne projektu speciální soubory?  
 Další rozhodnutí o návrhu důležité je, jestli strukturu projektu používá speciální soubory. Speciální soubory jsou skryté soubory, které tvoří základ soubory, které jsou viditelné v Průzkumníku řešení a v se změnami a rezervace dialogová okna. Pokud chcete použít speciální soubory, postupujte podle následujících pokynů:  
  
1.  Nepřidružujte speciální soubory s kořenového uzlu projektu – to znamená, s projektem samotném souboru. Soubor projektu musí být jeden soubor.  
  
2.  Při jsou speciální soubory přidat, odebrat nebo přejmenovat v projektu, odpovídající <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> musí být nastaven příznak, který označuje soubory jsou speciální soubory vyvolání událostí. Tyto události jsou volány prostředí v reakci na projekt volání odpovídající <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> metody.  
  
3.  Pokud projekt nebo editoru volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> pro soubor, speciální soubory přidružené k souboru nejsou rezervovány automaticky. Předejte speciální soubory v společně s nadřazeném souboru. Prostředí rozpozná vztah mezi všechny soubory, které se předávají v a odpovídajícím způsobem Skrýt speciální soubory v uživatelském rozhraní rezervace.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Podpora správy zdrojového kódu](../../extensibility/internals/supporting-source-control.md)