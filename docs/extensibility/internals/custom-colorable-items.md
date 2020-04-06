---
title: Vlastní barevné položky | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: feecd9e8f8178045f66999b775e2d0792f50b288
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709000"
---
# <a name="custom-colorable-items"></a>Vlastní barevné položky
Seznam typů pro vybarvení, například klíčová slova a komentáře, můžete přepsat implementací vlastních barevných položek jako součásti jazykové služby.

## <a name="user-settings-of-colorable-items"></a>Uživatelská nastavení barevných položek
 Dialogové okno **Písma a barvy** můžete zobrazit tak, že v nabídce **Nástroje** vyberete **Možnosti** a potom vyberete **Písma a barvy** v části **Prostředí**. Když vyberete zobrazení, například **Textový editor** nebo **příkazové okno**, zobrazí se v seznamu **Položky zobrazení** všechny obarvitelné položky pro toto zobrazení. Můžete zobrazit a změnit písmo, velikost, barvu popředí a barvu pozadí pro každou barevnou položku. Vaše volby jsou uloženy v mezipaměti v registru a přístupné podle názvu barevné položky.

## <a name="presentation-of-colorable-items"></a>Prezentace barevných položek
 Vzhledem k tomu, že rozhraní IDE zpracovává přepsání barevných položek uživatelem v dialogovém **okně Písma a barvy,** stačí zadat pouze každou vlastní barevnou položku s názvem. Tento název se zobrazí v seznamu **Zobrazit položky.** Barevné položky se zobrazí v abecedním pořadí. Chcete-li seskupit vlastní barevné položky své jazykové služby, můžete začít s každým názvem jazyka s názvem jazyka, například **NewLanguage - Comment** a **NewLanguage - Keyword**.

> [!CAUTION]
> Do názvu barevné položky byste měli zahrnout název jazyka, abyste předešli kolizím s existujícími barevnými názvy položek. Pokud během vývoje změníte název jedné z barevných položek, je nutné obnovit mezipaměť, která byla vytvořena při prvním přístupu k barevným položkám. Experimentální mezipaměť můžete obnovit pomocí nástroje **CreateExpInstance,** který je nainstalován se sadou Visual Studio SDK, obvykle v adresáři:
>
> *C:\Program Files (x86)\Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin*
>
> Chcete-li obnovit mezipaměť, zadejte **příkaz CreateExpInstance /Reset**. Další informace o **instanci CreateExpInstance**naleznete v [tématu Nástroj CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md).

 Na první položku v seznamu barevných položek se nikdy neodkazuje. První položka odpovídá indexu barevné položky 0 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a vždy poskytuje výchozí barvy textu a atributy pro tuto položku. Nejjednodušší způsob, jak se vypořádat s touto neodkazovnou položkou, je zadat zástupnou barevnou položku v seznamu jako první položku.

## <a name="implement-custom-colorable-items"></a>Implementace vlastních barevných položek

1. Definujte, co musí být vybarveno ve vašem jazyce, například Klíčové slovo, Operátor a Identifikátor.

2. Vytvořte výčet těchto barevných položek.

3. Přidružte typy tokenů vrácené z analyzátoru nebo skeneru k výčtovým hodnotám.

    Například hodnoty představující typy tokenů mohou být stejné hodnoty ve výčtu vlastních barevných položek.

4. Při implementaci <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metody v <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> objektu vyplňte seznam atributů hodnotami z vlastního výčtu barevných položek odpovídajících typům tokenů vráceným z analyzátoru nebo skeneru.

5. Ve stejné třídě, která <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> rozhraní, implementovat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>rozhraní a jeho dvě metody a .

6. Implementujte rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.

7. Pokud chcete podporovat 24bitové nebo vysoké hodnoty <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> barev, implementujte také rozhraní.

8. V objektu jazykové služby vytvořte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> seznam, který obsahuje objekty, jeden pro každou barevnou položku, kterou může analyzátor nebo skener identifikovat.

    Ke každé položce v seznamu můžete přistupovat pomocí odpovídající hodnoty z vlastního výčtu barevných položek. Použijte hodnoty výčtu jako index do seznamu. K první položce v seznamu se nikdy nepřistupuje, protože odpovídá výchozímu stylu textu, který [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se vždy zpracovává sám. Můžete to kompenzovat vložením zástupné barevné položky na začátek seznamu.

9. Při implementaci <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> metody vraťte počet položek v seznamu vlastních barevných položek.

10. Při implementaci <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metody vraťte požadovanou barevnou položku ze seznamu.

    Příklad implementace rozhraní a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> naleznete v tématu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>.

## <a name="see-also"></a>Viz také
- [Model služby staršího jazyka](../../extensibility/internals/model-of-a-legacy-language-service.md)
- [Syntaxe barvení ve vlastních editorech](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Vybarvení syntaxe ve službě starších jazyků](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementace vybarvení syntaxe](../../extensibility/internals/implementing-syntax-coloring.md)
- [Postup: Použití vestavěných barevných položek](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
