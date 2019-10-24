---
title: Barevné zvýrazňování syntaxe ve službě starší verze jazyka | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c00e70ed28a8086a87851b978eb7ee6d6077c009
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722980"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Barevné zvýrazňování syntaxe ve službě starší verze jazyka

Visual Studio používá službu pro obarvení barev k identifikaci prvků jazyka a jejich zobrazení se zadanými barvami v editoru.

## <a name="colorizer-model"></a>Model Colorizer
 Služba jazyka implementuje rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>, které pak používají editory. Tato implementace je samostatný objekt od jazykové služby, jak je znázorněno na následujícím obrázku:

 ![Obrázek Colorizer SVC](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> Vybarvení syntaxe služby je oddělené od obecného mechanismu sady Visual Studio pro Colorizing text. Další informace o obecném [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] mechanismu, který podporuje Colorizing, najdete v tématu [Použití písem a barev](../../extensibility/using-fonts-and-colors.md).

 Kromě Colorizer může služba jazyka poskytovat vlastní barevně vybarvené položky, které editor používá, a to tak, že poskytuje vlastní barvy. To lze provést implementací rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> na stejném objektu, který implementuje rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>. Vrátí počet vlastních barevně vybarvení, když Editor volá metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> a vrátí jednotlivou vlastní barevnou položku, když Editor volá metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.

 Metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> vrátí objekt, který implementuje rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>. Pokud jazyková služba podporuje 24bitové nebo vysoké hodnoty barev, musí implementovat rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> u stejného objektu jako <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> rozhraní.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Jak VSPackage používá jazykovou službu colorizer

1. Rozhraní VSPackage musí získat příslušnou jazykovou službu, která vyžaduje, aby služba jazyka VSPackage mohla provést následující akce:

    1. Použijte objekt implementující rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>, abyste získali text, který se má obarvit.

         Text se obvykle zobrazuje pomocí objektu, který implementuje rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.

    2. Získejte jazykovou službu pomocí dotazu poskytovatele služby VSPackage pro identifikátor GUID jazykové služby. Jazykové služby se identifikují v registru podle přípony souboru.

    3. Přidružte službu jazyka k <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> voláním její metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A>.

2. VSPackage nyní může získat a použít objekt Colorizer následujícím způsobem:

    > [!NOTE]
    > Sady VSPackage, které používají základní editor, nemusejí explicitně získávat Colorizer objekty jazykové služby. Jakmile instance základního editoru získá příslušnou jazykovou službu, provede všechny níže uvedené úlohy barev.

    1. Získejte objekt Colorizer jazykové služby, který implementuje rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> zavoláním metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> na objekt <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> jazykové služby.

    2. Voláním metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> získáte informace o colorizer pro konkrétní rozsah textu.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> vrátí pole hodnot, jeden pro každý znak v rozsahu textu, který je barevný. Hodnoty jsou indexy do seznamu barevně vybarvené položky, který je buď výchozím seznamem položek, který je udržován v základním editoru, nebo vlastním seznamem položek, který je spravován samotnými jazykovými službami.

    3. Použijte informace o vybarvení vrácené metodou <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> k zobrazení vybraného textu.

> [!NOTE]
> Kromě používání jazykové služby Colorizer může VSPackage použít také mechanizmus obarvení textu pro obecné účely sady Visual Studio. Další informace o tomto mechanismu najdete v tématu [Použití písem a barev](../../extensibility/using-fonts-and-colors.md).

## <a name="in-this-section"></a>V tomto oddílu
- [Implementace barevného zvýrazňování syntaxe](../../extensibility/internals/implementing-syntax-coloring.md)

 Popisuje způsob, jakým Editor přistupuje k barevnému zvýrazňování syntaxe služby jazyka a o tom, co jazyková služba musí implementovat, aby podporovala barevné zvýrazňování syntaxe.

- [Postupy: Použití předdefinovaných položek, které lze zabarvit](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 Ukazuje, jak použít předdefinované barevné položky z jazykové služby.

- [Vlastní položky, které lze zabarvit](../../extensibility/internals/custom-colorable-items.md)

 Popisuje, jak implementovat vlastní barevnou položku.

## <a name="see-also"></a>Viz také:

- [Použití písem a barev](../../extensibility/using-fonts-and-colors.md)