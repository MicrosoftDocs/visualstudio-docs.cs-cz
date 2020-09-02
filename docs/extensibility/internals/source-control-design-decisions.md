---
title: Rozhodnutí o návrhu správy zdrojových kódů | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705248"
---
# <a name="source-control-design-decisions"></a>Rozhodnutí o návrhu správy zdrojového kódu
Při implementaci správy zdrojových kódů by se měla vzít v úvahu následující rozhodnutí o návrhu pro projekty.

## <a name="will-information-be-shared-or-private"></a>Budou informace sdílené nebo soukromé?
 Nejdůležitějším rozhodnutím pro návrh můžete udělat, jaké informace lze sdílet a co je soukromé. Například seznam souborů pro projekt je sdílený, ale v tomto seznamu souborů mohou někteří uživatelé chtít mít soukromé soubory. Nastavení kompilátoru je sdílené, ale spouštěcí projekt je obecně soukromý. Nastavení jsou buď čistě sdílená, sdílená s přepsáním, nebo čistě soukromá. V rámci návrhu nejsou vráceny žádné položky, jako jsou například soubory možností uživatele řešení (. suo) [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] . Nezapomeňte uložit všechny soukromé informace v soukromých souborech, jako je například soubor. suo, nebo konkrétní soukromý soubor, který vytvoříte, například soubor. csproj. User pro soubor Visual C# nebo. vbproj. User pro Visual Basic.

 Toto rozhodnutí není vše včetně a může být provedeno na základě položky.

## <a name="will-the-project-include-special-files"></a>Bude projekt zahrnovat speciální soubory?
 Dalším důležitým rozhodnutím návrhu je, zda struktura projektu používá speciální soubory. Speciální soubory jsou skryté soubory, které jsou základem souborů, které jsou viditelné v Průzkumník řešení a v dialogových oknech pro vrácení se změnami a odhlášení. Pokud používáte speciální soubory, postupujte podle těchto pokynů:

1. Nepřidružte speciální soubory k kořenovému uzlu projektu – to znamená s samotným souborem projektu. Soubor projektu musí být jeden soubor.

2. Při přidání, odebrání nebo přejmenování speciálních souborů v projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> musí být aktivovány příslušné události se sadou příznaků, která označuje, že soubory jsou speciální soubory. Tyto události jsou volány prostředím v reakci na projekt volající příslušné <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> metody.

3. Když váš projekt nebo editor volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> soubor, speciální soubory přidružené k tomuto souboru nejsou automaticky rezervovány. Předání speciálních souborů společně s nadřazeným souborem. Prostředí zjistí vztah mezi všemi soubory, které jsou předány, a patřičně skryje speciální soubory v uživatelském rozhraní rezervace.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Podpora správy zdrojového kódu](../../extensibility/internals/supporting-source-control.md)
