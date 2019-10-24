---
title: Rozhodnutí o návrhu správy zdrojových kódů | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a7c8a902520323f548a7dd77a84b07a56bfc9a0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723619"
---
# <a name="source-control-design-decisions"></a>Rozhodnutí o návrhu správy zdrojového kódu
Při implementaci správy zdrojových kódů by se měla vzít v úvahu následující rozhodnutí o návrhu pro projekty.

## <a name="will-information-be-shared-or-private"></a>Budou informace sdílené nebo soukromé?
 Nejdůležitějším rozhodnutím pro návrh můžete udělat, jaké informace lze sdílet a co je soukromé. Například seznam souborů pro projekt je sdílený, ale v tomto seznamu souborů mohou někteří uživatelé chtít mít soukromé soubory. Nastavení kompilátoru je sdílené, ale spouštěcí projekt je obecně soukromý. Nastavení jsou buď čistě sdílená, sdílená s přepsáním, nebo čistě soukromá. Návrh, soukromé položky, například soubory možností uživatele řešení (. suo), nejsou vráceny do [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]. Nezapomeňte uložit všechny soukromé informace v privátních souborech, jako je například soubor. suo, nebo konkrétní soukromý soubor, který vytvoříte, například soubor. csproj. User pro soubor Visual C# nebo. vbproj. user pro Visual Basic.

 Toto rozhodnutí není vše včetně a může být provedeno na základě položky.

## <a name="will-the-project-include-special-files"></a>Bude projekt zahrnovat speciální soubory?
 Dalším důležitým rozhodnutím návrhu je, zda struktura projektu používá speciální soubory. Speciální soubory jsou skryté soubory, které jsou základem souborů, které jsou viditelné v Průzkumník řešení a v dialogových oknech pro vrácení se změnami a odhlášení. Pokud používáte speciální soubory, postupujte podle těchto pokynů:

1. Nepřidružte speciální soubory k kořenovému uzlu projektu – to znamená s samotným souborem projektu. Soubor projektu musí být jeden soubor.

2. Při přidání, odebrání nebo přejmenování speciálních souborů v projektu musí být vyvolány příslušné události <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> se sadou příznaků, která označuje, že soubory jsou speciální soubory. Tyto události jsou volány prostředím v reakci na projekt volající příslušné metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>.

3. Když projekt nebo editor volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> pro soubor, speciální soubory přidružené k tomuto souboru nejsou automaticky rezervovány. Předání speciálních souborů společně s nadřazeným souborem. Prostředí zjistí vztah mezi všemi soubory, které jsou předány, a patřičně skryje speciální soubory v uživatelském rozhraní rezervace.

## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Podpora správy zdrojového kódu](../../extensibility/internals/supporting-source-control.md)