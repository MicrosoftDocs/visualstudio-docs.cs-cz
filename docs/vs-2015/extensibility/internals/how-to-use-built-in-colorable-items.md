---
title: 'Postupy: použití předdefinovaných položek které lze zabarvit | Dokumentace Microsoftu'
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
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9b168eee5f5f8a8a9775d9326cb9a7dda6287792
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51806084"
---
# <a name="how-to-use-built-in-colorable-items"></a>Postupy: použití předdefinovaných položek které lze zabarvit
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Než použijete integrovanou které lze zabarvit položky, můžete musí nejprve signalizuje, že do integrovaného vývojového prostředí (IDE), že nejsou poskytnutí vlastní vlastní které lze zabarvit položek, které v tomto případě by byly <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> objekty. To provedete tak, že nastavíte položku registru pro službu jazyka.  
  
### <a name="to-use-built-in-colorable-items"></a>Použití předdefinovaných položek které lze zabarvit  
  
1.  V části HKEY_LOCAL_MACHINE\VisualStudio\\*X.Y*\Languages\Language služby\\*název jazyka*, kde *X.Y* je verze [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a *název jazyka* je název jazyka, vytvořit vstupní hodnotu registru DWORD s názvem `RequestStockColors`.  
  
2.  Nastavte `RequestStockColors` hodnotu položky registru na 1.  
  
     Po vytvoření položka registru, vaše colorizer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metoda může použít jako objekty její členové <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> výčet k vyplnění pole barevnými atributy pro použití v editoru.  
  
    > [!NOTE]
    >  Pokud poskytujete vlastní, které lze zabarvit položky není nastavený této položky registru. Další informace najdete v tématu [vlastní, které lze zabarvit položky](../../extensibility/internals/custom-colorable-items.md).  
  
## <a name="see-also"></a>Viz také  
 [Barevné zvýrazňování syntaxe ve vlastních editorech](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementace barevného zvýrazňování syntaxe](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Vlastní položky které lze zabarvit](../../extensibility/internals/custom-colorable-items.md)   
 [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service2.md)

