---
title: Barevné zvýrazňování syntaxe ve službě starší verze jazyka | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d0cc0dcf40ab9231e3af6208ab2f844c69f3398
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/06/2020
ms.locfileid: "93414552"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Barevné zvýrazňování syntaxe ve službě starší verze jazyka

Visual Studio používá službu pro obarvení barev k identifikaci prvků jazyka a jejich zobrazení se zadanými barvami v editoru.

## <a name="colorizer-model"></a>Model Colorizer
 Jazyková služba implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> rozhraní, které pak používají editory. Tato implementace je samostatný objekt od jazykové služby, jak je znázorněno na následujícím obrázku:

 ![Obrázek Colorizer SVC](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> Vybarvení syntaxe služby je oddělené od obecného mechanismu sady Visual Studio pro Colorizing text. Další informace o obecném [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] mechanismu, který podporuje Colorizing, najdete v tématu [Použití písem a barev](/previous-versions/visualstudio/visual-studio-2015/extensibility/using-fonts-and-colors?preserve-view=true&view=vs-2015).

 Kromě Colorizer může služba jazyka poskytovat vlastní barevně vybarvené položky, které editor používá, a to tak, že poskytuje vlastní barvy. To lze provést implementací <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> rozhraní na stejném objektu, který implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> rozhraní. Vrátí počet vlastních barevně vybarvení, když Editor volá <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> metodu a vrátí jednotlivou vlastní barevnou položku, když Editor volá <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metodu.

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>Metoda vrátí objekt, který implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> rozhraní. Pokud jazyková služba podporuje 24bitové nebo vysoké hodnoty barev, musí implementovat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> rozhraní na stejném objektu jako <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> rozhraní.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Jak VSPackage používá jazykovou službu colorizer

1. Rozhraní VSPackage musí získat příslušnou jazykovou službu, která vyžaduje, aby služba jazyka VSPackage mohla provést následující akce:

    1. Použijte objekt implementující <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> rozhraní, abyste získali text, který se má obarvit.

         Text se obvykle zobrazuje pomocí objektu, který implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> rozhraní.

    2. Získejte jazykovou službu pomocí dotazu poskytovatele služby VSPackage pro identifikátor GUID jazykové služby. Jazykové služby se identifikují v registru podle přípony souboru.

    3. Přidružte službu jazyka pomocí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metody.

2. VSPackage nyní může získat a použít objekt Colorizer následujícím způsobem:

    > [!NOTE]
    > Sady VSPackage, které používají základní editor, nemusejí explicitně získávat Colorizer objekty jazykové služby. Jakmile instance základního editoru získá příslušnou jazykovou službu, provede všechny níže uvedené úlohy barev.

    1. Získejte objekt Colorizer jazykové služby, který implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> rozhraní a, voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metody v objektu jazykové služby <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> .

    2. Voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metody získáte informace o colorizer pro konkrétní rozsah textu.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Vrátí pole hodnot, jeden pro každý znak v rozsahu textu, který je barevný. Hodnoty jsou indexy do seznamu barevně vybarvené položky, který je buď výchozím seznamem položek, který je udržován v základním editoru, nebo vlastním seznamem položek, který je spravován samotnými jazykovými službami.

    3. Použijte informace o vybarvení vrácené <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodou k zobrazení vybraného textu.

> [!NOTE]
> Kromě používání jazykové služby Colorizer může VSPackage použít také mechanizmus obarvení textu pro obecné účely sady Visual Studio. Další informace o tomto mechanismu najdete v tématu [Použití písem a barev](/previous-versions/visualstudio/visual-studio-2015/extensibility/using-fonts-and-colors?preserve-view=true&view=vs-2015).

## <a name="in-this-section"></a>V tomto oddílu
- [Implementace barevného zvýrazňování syntaxe](../../extensibility/internals/implementing-syntax-coloring.md)

 Popisuje způsob, jakým Editor přistupuje k barevnému zvýrazňování syntaxe služby jazyka a o tom, co jazyková služba musí implementovat, aby podporovala barevné zvýrazňování syntaxe.

- [Postupy: Použití předdefinovaných položek, které lze zabarvit](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 Ukazuje, jak použít předdefinované barevné položky z jazykové služby.

- [Vlastní položky, které lze zabarvit](../../extensibility/internals/custom-colorable-items.md)

 Popisuje, jak implementovat vlastní barevnou položku.