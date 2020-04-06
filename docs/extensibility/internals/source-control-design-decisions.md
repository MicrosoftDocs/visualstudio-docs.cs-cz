---
title: Rozhodnutí o návrhu kontroly zdrojového kódu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c36bb2b50a72a52aeaeb7712f4ed711845b5e6d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705248"
---
# <a name="source-control-design-decisions"></a>Rozhodnutí o návrhu správy zdrojového kódu
Následující rozhodnutí o návrhu by měly být považovány za projekty při provádění správy zdrojového kódu.

## <a name="will-information-be-shared-or-private"></a>Budou informace sdíleny nebo soukromé?
 Nejdůležitější rozhodnutí o návrhu, které můžete udělat, je to, jaké informace jsou sharable a co je soukromé. Například seznam souborů pro projekt je sdílen, ale v rámci tohoto seznamu souborů, někteří uživatelé mohou chtít mít soukromé soubory. Nastavení kompilátoru jsou sdíleny, ale spuštění projektu je obecně soukromé. Nastavení jsou čistě sdílená, sdílená s přepsáním nebo čistě soukromá. Podle návrhu soukromé položky, jako je například možnosti řešení uživatelské [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)](.suo) soubory, nejsou kontrolovány do . Nezapomeňte uložit všechny soukromé informace v soukromých souborech, jako je soubor .suo nebo konkrétní soukromý soubor, který vytvoříte, například soubor .csproj.user pro visual c# nebo soubor .vbproj.user pro jazyk Visual Basic.

 Toto rozhodnutí není all-inclusive a může být provedeno na základě položky po položkách.

## <a name="will-the-project-include-special-files"></a>Bude projekt obsahovat speciální soubory?
 Dalším důležitým rozhodnutím o návrhu je, zda struktura projektu používá speciální soubory. Speciální soubory jsou skryté soubory, které jsou základem souborů, které jsou viditelné v Průzkumníku řešení a v dialogových oknech vrácení se změnami a rezervování. Pokud používáte speciální soubory, postupujte podle následujících pokynů:

1. Nepřidružujte speciální soubory ke kořenovému uzlu projektu – to znamená k samotnému souboru projektu. Soubor projektu musí být jeden soubor.

2. Při přidání, odebrání nebo přejmenování speciálních souborů v <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> projektu musí být příslušné události aktivovány se sadou příznaku, která označuje, že soubory jsou speciální soubory. Tyto události jsou volány prostředí v reakci <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> na projekt volání příslušné metody.

3. Když váš projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> nebo editor volá soubor, speciální soubory přidružené k tomuto souboru nejsou automaticky rezervovány. Předajte speciální soubory spolu s nadřazeným souborem. Prostředí rozpozná vztah mezi všemi soubory, které jsou předány a odpovídajícím způsobem skrýt speciální soubory v příkazu rezervovat.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Podpora správy zdrojového kódu](../../extensibility/internals/supporting-source-control.md)
