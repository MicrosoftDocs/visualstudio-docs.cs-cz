---
title: Vlastní barevné položky | Microsoft Docs
description: Naučte se vytvářet vlastní barevné položky jako součást služby jazyka přepsáním položek v dialogovém okně písma a barvy, jako jsou klíčová slova a komentáře.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f08c5c9e533e3a21ec4b87e7d148c3022ee0fed1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056792"
---
# <a name="custom-colorable-items"></a>Vlastní barevné položky
Můžete přepsat seznam typů pro Colorizing, jako jsou klíčová slova a komentáře, implementací vlastních barevně vypsaných položek jako součást vaší jazykové služby.

## <a name="user-settings-of-colorable-items"></a>Uživatelské nastavení barevných položek
 Můžete zobrazit dialogové okno **písma a barvy** výběrem možnosti v nabídce **nástroje** a následným výběrem **Možnosti** **písma a barvy** v části **prostředí**. Když vyberete zobrazení, například **textový editor** nebo **příkazové okno**, zobrazí se v seznamu **položky zobrazení** všechny barvy, které lze zobrazit. Můžete zobrazit a změnit písmo, velikost, barvu popředí a barvu pozadí pro každou položku barev. Vaše volby se ukládají do mezipaměti v registru a jsou dostupné pro barevný název položky.

## <a name="presentation-of-colorable-items"></a>Prezentace barevně vydaných položek
 Vzhledem k tomu, že rozhraní IDE zpracovává přepsání barev uživatelem v dialogovém okně **písma a barvy** , potřebujete pouze každou vlastní barevnou položku s názvem. Tento název se zobrazí v seznamu **položky zobrazení** . Vybarvení položek se zobrazí v abecedním pořadí. Chcete-li seskupit vlastní barevné položky vaší jazykové služby, můžete začít s názvem jazyka, například **NewLanguage-Comment** a **NewLanguage-klíčové slovo**.

> [!CAUTION]
> V názvu barevné položky byste měli zahrnout název jazyka, abyste se vyhnuli kolizím s existujícími názvy položek barev. Pokud změníte název jedné z položek barev během vývoje, musíte resetovat mezipaměť, která byla vytvořena při prvním použití barevně vydaných položek. Experimentální mezipaměť můžete obnovit pomocí nástroje **CreateExpInstance** , který je nainstalován se sadou Visual Studio SDK, obvykle v adresáři:
>
> *C:\Program Files (x86) \Microsoft Visual Studio 14.0 \ VSSDK\VisualStudioIntegration\Tools\Bin*
>
> Mezipaměť resetujete tak, že zadáte **CreateExpInstance/reset po vyčištění**. Další informace o **CreateExpInstance** najdete v tématu [CreateExpInstance Utility](../../extensibility/internals/createexpinstance-utility.md).

 Na první položku v seznamu položek, na které jsou barvy, se nikdy neodkazuje. První položka odpovídá indexu položek s barvou 0 a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vždy poskytuje výchozí barvy textu a atributy pro tuto položku. Nejjednodušší způsob, jak se vypořádat s touto neodkaznou položkou, je dodat v seznamu zástupnou položku s barvou barvy jako první položku.

## <a name="implement-custom-colorable-items"></a>Implementace vlastních barevně vydaných položek

1. Definujte, co musí být zabarvení v jazyce, například klíčové slovo, operátor a identifikátor.

2. Vytvořte výčet těchto položek barev.

3. Přidružte typy tokenů vrácené z analyzátoru nebo skeneru k výčtovým hodnotám.

    Například hodnoty reprezentující typy tokenů mohou být stejné hodnoty ve výčtu vlastních vybarvenéch položek.

4. V implementaci <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metody v <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> objektu vyplní seznam atributů hodnotami z vlastního výčtu položek, které odpovídají typům tokenů vráceným z analyzátoru nebo skeneru.

5. Ve stejné třídě, která implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> rozhraní, implementujte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> rozhraní a jeho dvě metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> .

6. Implementujte rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.

7. Pokud chcete podporovat 24bitové nebo vysoké hodnoty barev, implementujte také <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> rozhraní.

8. V objektu jazykové služby vytvořte seznam obsahující vaše <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> objekty, jednu pro každou barevnou položku, kterou může váš analyzátor nebo skener identifikovat.

    K jednotlivým položkám v seznamu můžete přistupovat pomocí odpovídající hodnoty z výčtu vlastních vybarvenéch položek. Použijte hodnoty výčtu jako index do seznamu. První položka v seznamu nikdy neproběhla, protože odpovídá výchozímu stylu textu, který se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vždy sám zpracovává. Můžete to kompenzovat vložením zástupné položky barvy na začátek seznamu.

9. V implementaci <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> metody vrátí počet položek v seznamu vlastních položek barevně.

10. V implementaci <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metody vraťte požadovanou barevnou položku ze seznamu.

    Příklad implementace <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> rozhraní a naleznete v tématu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> .

## <a name="see-also"></a>Viz také
- [Model služby starší verze jazyka](../../extensibility/internals/model-of-a-legacy-language-service.md)
- [Barevné zvýrazňování syntaxe ve vlastních editorech](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementovat barvy syntaxe](../../extensibility/internals/implementing-syntax-coloring.md)
- [Postupy: Použití vestavěných barevných položek](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
