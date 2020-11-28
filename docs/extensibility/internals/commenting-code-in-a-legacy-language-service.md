---
title: Komentování kódu ve službě starší verze jazyka | Microsoft Docs
description: Přečtěte si o třídách "MPF (Managed Package Framework), které poskytují podporu pro komentování kódu ve službě starší verze jazyka v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07205a8e15cd338fa1acf0d3b081301a083bba5d
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304995"
---
# <a name="comment-code-in-a-legacy-language-service"></a>Kód komentáře ve službě starší verze jazyka
Programovací jazyky obvykle poskytují způsob, jak opatřit poznámky nebo komentovat kód. Komentář je část textu, která poskytuje další informace o kódu, ale je ignorována během kompilace nebo výkladu.

 Třídy spravovaného balíčku architektury (MPF) poskytují podporu pro přidávání komentářů a odkomentování vybraného textu.

## <a name="comment-styles"></a>Styly komentářů
Existují dva obecné styly komentářů:

1. Komentáře k řádku, kde je komentář na jednom řádku.

2. Zablokuje komentáře, kde komentář může obsahovat více řádků.

Komentáře k řádkům obvykle mají počáteční znak (nebo znaky), zatímco komentáře bloku mají jak počáteční, tak koncové znaky. Například v jazyce C# začíná řádkový komentář `//` a komentář bloku začíná `/*` a končí na `*/` .

Když uživatel vybere příkaz pro **Výběr komentáře** z nabídky **Upravit**  >  **Upřesnit** , příkaz se směruje do <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> metody <xref:Microsoft.VisualStudio.Package.Source> třídy. Když uživatel vybere příkaz pro zrušení **komentáře výběru**, je příkaz směrován do <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> metody.

## <a name="support-code-comments"></a>Komentáře k kódu podpory
 Je možné, že vaše jazyková služba podporuje komentáře kódu prostřednictvím `EnableCommenting` pojmenovaného parametru <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Tím se nastaví <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> vlastnost <xref:Microsoft.VisualStudio.Package.LanguagePreferences> třídy. Další informace o nastavení funkcí jazykové služby najdete v tématu [Registrace starší verze jazykové služby](../../extensibility/internals/registering-a-legacy-language-service1.md).

 Musíte také přepsat <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> metodu pro vrácení <xref:Microsoft.VisualStudio.Package.CommentInfo> struktury se znaky komentáře pro váš jazyk. Znaky komentáře řádku ve stylu jazyka C# jsou výchozí.

### <a name="example"></a>Příklad
 Zde je příklad implementace <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> metody.

```csharp
using Microsoft.VisualStudio.Package;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        public override CommentInfo GetCommentFormat() {
            CommentInfo info = new CommentInfo();
            info.LineStart       = "//";
            info.BlockStart      = "/*";
            info.BlockEnd        = "*/";
            info.UseLineComments = true;
            return info;
        }
    }
}
```

## <a name="see-also"></a>Viz také
- [Funkce služby starší verze jazyka](../../extensibility/internals/legacy-language-service-features1.md)
- [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)
