---
title: 'Postupy: použití Built-In barevně vydaných položek | Microsoft Docs'
description: Naučte se používat vestavěné barevné položky v integrovaném vývojovém prostředí (IDE) sady Visual Studio pro vaši jazykovou službu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 253c108fe83eaf44f945f546bd64dd6529de1dd6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086076"
---
# <a name="how-to-use-built-in-colorable-items"></a>Postupy: Použití vestavěných barevných položek
Než začnete používat vestavěné položky barev, musíte nejdřív signalizovat integrované vývojové prostředí (IDE), které neposkytujete vlastní barvy, které by v tomto případě byly <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> objekty. Provedete to tak, že nastavíte položku registru pro službu jazyka.

## <a name="to-use-built-in-colorable-items"></a>Použití vestavěných barevných položek

1. V části **HKEY_LOCAL_MACHINE\VisualStudio\\<X. Y> \languages\language Services \\<název \> jazyka**, kde \<X.Y> je verze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a \<Language Name> je název vašeho jazyka, vytvořte hodnotu položky registru DWORD s názvem **RequestStockColors**.

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
