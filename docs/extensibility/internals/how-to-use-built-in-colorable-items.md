---
title: 'Postupy: Použití vestavěných barevně používaných položek | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 762d1e53f7aafa11ed345859e68fc98766eec77d
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905219"
---
# <a name="how-to-use-built-in-colorable-items"></a>Postupy: Použití vestavěných barevných položek
Než začnete používat vestavěné položky barev, musíte nejdřív signalizovat integrované vývojové prostředí (IDE), které neposkytujete vlastní barvy, které by v tomto případě byly <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> objekty. Provedete to tak, že nastavíte položku registru pro službu jazyka.

## <a name="to-use-built-in-colorable-items"></a>Použití vestavěných barevných položek

1. V části **HKEY_LOCAL_MACHINE \visualstudio \\<X. Y> \languages\language Services \\<název \> jazyka**, kde \<X.Y> je verze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a \<Language Name> je název vašeho jazyka, vytvořte hodnotu položky registru DWORD s názvem **RequestStockColors**.

2. Nastavte položku registru **RequestStockColors** na hodnotu *1*.

    Po vytvoření položky registru <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> může metoda Colorizer použít členy <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> výčtu k vyplnění pole atributů barvy pro použití v editoru.

   > [!NOTE]
   > Nenastavte tuto položku registru, Pokud poskytujete vlastní barevné položky. Další informace najdete v tématu [vlastní barevné položky](../../extensibility/internals/custom-colorable-items.md).

## <a name="see-also"></a>Viz také
- [Barevné zvýrazňování syntaxe ve vlastních editorech](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementace Obarvení syntaxe](../../extensibility/internals/implementing-syntax-coloring.md)
- [Vlastní barevné položky](../../extensibility/internals/custom-colorable-items.md)
- [Registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service2.md)
