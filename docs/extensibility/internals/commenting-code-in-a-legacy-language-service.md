---
title: Kód komentářů ve službě starší verze jazyka | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3a4215d3ea841f8e7c7c9f057535d9585682dcfa
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510459"
---
# <a name="comment-code-in-a-legacy-language-service"></a>Kód komentářů ve službě starší verze jazyka
Programovací jazyky obvykle poskytují způsob poznámky nebo komentáře kódu. Komentář je část textu, který poskytuje další informace o kódu, ale je ignorována během kompilace a interpretace.  
  
 Třídy spravované balíčku rozhraní framework (MPF) poskytují podporu pro přidávání poznámek a odstraňuje se komentování vybraného textu.  
  
## <a name="comment-styles"></a>Styly komentář  
Existují dvě obecné styly komentář:  
   
1.  Řádek komentáře, kde komentář je na jednom řádku.  
  
2.  Komentáře bloku, ve kterém komentář může obsahovat více řádků.  
  

Komentářů řádku mají obvykle počáteční znak (nebo znaky), při komentáře bloku mají počátečních a koncových znaků. Například v jazyce C#, řádkový komentář začíná `//`, a blok komentáře začíná `/*` a končí `*/`.  
  
Když uživatel vybere příkaz **Zakomentovat výběr** z **upravit** > **Upřesnit** nabídky, příkaz se směruje na <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> metodu <xref:Microsoft.VisualStudio.Package.Source> třídy. Když uživatel vybere příkaz **Odkomentovat výběr**, příkaz se směruje na <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> metody.  
  
## <a name="support-code-comments"></a>Komentáře kódu  
 Komentáře jazyka služby podpory kód prostřednictvím může mít `EnableCommenting` s názvem parametru <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Tím se nastaví <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> vlastnost <xref:Microsoft.VisualStudio.Package.LanguagePreferences> třídy. Další informace o nastavení jazyka funkce služby, najdete v části [registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
 Musí také přepsat <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> metodu pro návrat <xref:Microsoft.VisualStudio.Package.CommentInfo> strukturu s znaky komentáře pro váš jazyk. C# – znaky komentáře styl čáry jsou výchozí.  
  
### <a name="example"></a>Příklad  
 Tady je příklad implementace <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> metody.  
  
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
  
## <a name="see-also"></a>Viz také:  
 [Funkce služby starší verze jazyka](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service1.md)