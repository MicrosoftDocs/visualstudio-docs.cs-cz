---
title: Zbarvení syntaxe ve službě staršího jazyka | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 2589ec24f230287306e0ff7e802d381fb6ab18b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704760"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Barevné zvýrazňování syntaxe ve službě starší verze jazyka

Visual Studio používá službu barvení k identifikaci prvků jazyka a jejich zobrazení s určenými barvami v editoru.

## <a name="colorizer-model"></a>Model colorizeru
 Služba jazyka implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> rozhraní, které je pak používá no editory. Tato implementace je samostatný objekt od služby jazyka, jak je znázorněno na následujícím obrázku:

 ![SVC Colorizer grafika](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> Služba barvení syntaxe je oddělená od obecného mechanismu sady Visual Studio pro barvení textu. Další informace o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] obecném mechanismu podporujícím barvení naleznete [v tématu Použití písem a barev](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

 Kromě colorizer, jazyková služba může dodávat vlastní colorable položky, které jsou používány v editoru, reklamou, že dodává vlastní barevné položky. Můžete to provést implementací <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> rozhraní na stejný objekt, který implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> rozhraní. Vrátí počet vlastních barevných položek, když <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> editor volá metodu a vrátí jednotlivé vlastní colorable položky při editoru volá metodu. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>

 Metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> vrátí objekt, který <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> implementuje rozhraní. Pokud služba jazyka podporuje 24bitové nebo vysoké barevné <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> hodnoty, musí implementovat rozhraní na stejném objektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> jako rozhraní.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Jak VSPackage používá colorizer služby jazyka

1. VSPackage musí získat příslušnou jazykovou službu, která vyžaduje, aby jazyková služba VSPackage provést následující:

    1. Pomocí objektu implementujícího <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> rozhraní získejte barevný text.

         Text je obvykle zobrazen pomocí objektu, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> který implementuje rozhraní.

    2. Získejte jazykovou službu dotazem na poskytovatele služeb VSPackage pro identifikátor GUID služby jazyka. Jazykové služby jsou v registru identifikovány příponou souboru.

    3. Přidružte jazykovou službu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> k volání její <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metody.

2. VSPackage nyní můžete získat a použít colorizer objekt takto:

    > [!NOTE]
    > VSPackages, které používají editor jádra nemusí získat jazyk služby colorizer objekty explicitně. Jakmile instance editoru jádra získá příslušnou jazykovou službu, provede všechny zde uvedené úlohy vybarvení.

    1. Získejte objekt colorizer služby jazyka, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>který <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> implementuje , <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> a rozhraní, voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> metody na objektu služby jazyka.

    2. Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metody k získání informací o colorizer pro konkrétní rozsah textu.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>vrátí pole hodnot, jeden pro každý znak v rozsahu textu, který je obarven. Hodnoty jsou indexy do seznamu barevných položek, který je buď výchozí barevný seznam položek udržován a základní editor nebo vlastní barevný seznam položek udržuje jazyková služba sama.

    3. K zobrazení vybraného textu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> použijte informace o vybarvení vrácené metodou.

> [!NOTE]
> Kromě použití promítač služby jazyka, VSPackage můžete také použít univerzální Visual Studio mechanismus barvení textu. Další informace o tomto mechanismu naleznete [v tématu Použití písem a barev](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015).

## <a name="in-this-section"></a>V tomto oddílu
- [Implementace barevného zvýrazňování syntaxe](../../extensibility/internals/implementing-syntax-coloring.md)

 Popisuje, jak editor přistupuje k syntaxi zbarvení jazykové služby a co musí služba jazyka implementovat pro podporu zbarvení syntaxe.

- [Postupy: Použití předdefinovaných položek, které lze zabarvit](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 Ukazuje, jak používat předdefinované barevné položky ze služby jazyka.

- [Vlastní položky, které lze zabarvit](../../extensibility/internals/custom-colorable-items.md)

 Popisuje, jak implementovat vlastní barevné položky.
