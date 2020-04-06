---
title: Přidání kódu za komentáře ve službě staršího jazyka | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 5450199fde29f581dafdf9b2884c88ef26ea4ce7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709438"
---
# <a name="comment-code-in-a-legacy-language-service"></a>Kód komentáře ve službě starších jazyků
Programovací jazyky obvykle poskytují prostředky k oslnění nebo komentář kód. Komentář je část textu, která poskytuje další informace o kódu, ale je ignorována během kompilace nebo interpretace.

 Třídy Framework spravovaného balíčku (MPF) poskytují podporu pro komentování a odkomentování vybraného textu.

## <a name="comment-styles"></a>Styly komentářů
Existují dva obecné styly komentáře:

1. Komentáře řádku, kde je komentář na jednom řádku.

2. Blokovat komentáře, kde komentář může obsahovat více řádků.

Komentáře řádku mají obvykle počáteční znak (nebo znaky), zatímco blokové komentáře mají počáteční i koncové znaky. Například v c#, řádek komentář `//`začíná a poznámky `/*` bloku `*/`začíná a končí .

Když uživatel vybere příkaz **Výběr poznámek** z nabídky **Upravit** > **upřesnit,** <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> příkaz je <xref:Microsoft.VisualStudio.Package.Source> směrován na metodu třídy. Když uživatel vybere příkaz **Odkomentovat výběr**, příkaz <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> je směrován k metodě.

## <a name="support-code-comments"></a>Komentáře kódu podpory
 Komentáře kódu podpory jazykové služby můžete `EnableCommenting` mít pomocí <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> pojmenovaného parametru . Tím nastavíte <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> <xref:Microsoft.VisualStudio.Package.LanguagePreferences> vlastnost třídy. Další informace o nastavení funkcí služby jazyka naleznete v [tématu Registrace služby starších jazyků](../../extensibility/internals/registering-a-legacy-language-service1.md).

 Je také nutné <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> přepsat metodu <xref:Microsoft.VisualStudio.Package.CommentInfo> vrátit strukturu s znaky komentáře pro váš jazyk. C#-style znaky komentářů řádku jsou výchozí.

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
- [Funkce služby starších jazyků](../../extensibility/internals/legacy-language-service-features1.md)
- [Registrace služby staršího jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)
