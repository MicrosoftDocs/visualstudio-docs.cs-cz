---
title: Vlastní položky které lze zabarvit | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 037cd62bea7051e8341101a888bd428b7f78e828
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878794"
---
# <a name="custom-colorable-items"></a>Vlastní položky které lze zabarvit
Seznam typů můžete přepsat pro barevné označování, jako jsou klíčová slova a komentáře, díky implementaci vlastní, které lze zabarvit položky jako součást služby jazyka.  
  
## <a name="user-settings-of-colorable-items"></a>Uživatelská nastavení položek, které lze zabarvit  
 Můžete zobrazit **písma a barvy** dialogové okno tak, že vyberete **možnosti** na **nástroje** nabídky a následným výběrem **písma a barvy** v části **prostředí**. Když vyberte zobrazení, jako je například **textový Editor** nebo **příkazové okno**, **zobrazení položek** seznamu jsou uvedeny všechny které lze zabarvit položky, které zobrazují. Můžete zobrazit a změnit písmo, velikost, barvu popředí a barva pozadí pro každou položku které lze zabarvit. Vaše volby jsou uloženy v mezipaměti v registru a přistupuje, které lze zabarvit název.  
  
## <a name="presentation-of-colorable-items"></a>Prezentace položek, které lze zabarvit  
 Protože zpracovává přepsání uživatele, které lze zabarvit položek v rozhraní IDE **písma a barvy** dialogové okno, je nutné zadat pouze položky vlastní které lze zabarvit s názvem. Tento název se, co se zobrazuje **zobrazení položek** seznamu. Zobrazí položky, které lze zabarvit v abecedním pořadí. K seskupení vlastní služba jazyka, které lze zabarvit položky, můžete začít názvem název jazyka, například **NewLanguage - komentář** a **NewLanguage – klíčové slovo**.  
  
> [!CAUTION]
>  V které lze zabarvit název pro zabránění kolizím s existující názvy, které lze zabarvit položky, měli byste zahrnout název jazyka. Pokud změníte název jedné z položek aplikace které lze zabarvit během vývoje, je nutné obnovit, který byl vytvořen při prvním získal přístup k které lze zabarvit položky mezipaměti. Můžete resetovat experimentální mezipaměť **CreateExpInstance** nástroj, který se instaluje se sadou Visual Studio SDK, obvykle v adresáři:  
>   
>  *C:\Program soubory (x86) \Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin*
>   
>  Chcete-li obnovit mezipaměť, zadejte **/reset CreateExpInstance**. Další informace o **CreateExpInstance**, naleznete v tématu [nástroj CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md).  
  
 První položka v seznamu položek, které lze zabarvit nikdy odkazován. První položka odpovídá na 0, které lze zabarvit položky index a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vždy poskytuje výchozí barvy textu a atributy pro danou položku. Nejjednodušší způsob práci s touto položkou neodkazovaná je zadat zástupný symbol které lze zabarvit položku v seznamu jako první položku.  
  
## <a name="implement-custom-colorable-items"></a>Implementovat vlastní položky které lze zabarvit  
  
1. Definujte, co musí barevně zvýrazněné v jazyce, třeba – klíčové slovo, operátor a identifikátor.  
  
2. Vytvořte výčet těchto položek, které lze zabarvit.  
  
3. Přiřaďte typy tokenů vrátil z analyzátor a skener s výčtové hodnoty.  
  
    Hodnoty, představující typy tokenů může být například stejné hodnoty, které lze zabarvit vlastní položky výčtu.  
  
4. Ve vaší implementaci <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metoda ve vaší <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> objektu, naplnění seznamu atributy s hodnotami z vaší vlastní, které lze zabarvit položky výčtu odpovídající typy tokenů vrátil analyzátor a skener.  
  
5. Ve stejné třídě, která implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> rozhraní, implementujte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> rozhraní a jeho dvě metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.  
  
6. Implementace <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> rozhraní.  
  
7. Pokud chcete zajistit podporu barvu 24-bit nebo vysoké hodnoty, implementovat taky <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> rozhraní.  
  
8. V objektu služby jazyka, vytvořte seznam, který obsahuje vaše <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> objekty, pro které lze zabarvit položky můžete určit analyzátor a skener.  
  
    Každá položka v seznamu můžete přistupovat pomocí odpovídající hodnotu z výčtu vlastní, které lze zabarvit položky. Použijte hodnoty výčtu jako index do seznamu. Nikdy je nevyužili první položku v seznamu, protože výchozí text odpovídá stylu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vždy zpracovává samotný. To se může kompenzovat vložením které lze zabarvit položky zástupný text na začátku seznamu.  
  
9. Ve vaší implementaci <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> metody, vrátí počet položek, které ve vaší vlastní, které lze zabarvit položky seznamu.  
  
10. Ve vaší implementaci <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metodu, vrací požadovaná které lze zabarvit položku ze seznamu.  
  
    Příklad toho, jak implementovat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> rozhraní, naleznete v tématu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>.  
  
## <a name="see-also"></a>Viz také:  
 [Model služby starší verze jazyka](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [Barevné zvýrazňování syntaxe ve vlastních editorech](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Barevné zvýrazňování syntaxe implementace](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Postupy: použití předdefinovaných položek které lze zabarvit](../../extensibility/internals/how-to-use-built-in-colorable-items.md)