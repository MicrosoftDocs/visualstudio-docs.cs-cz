---
title: 'Postup: Použití předdefinovaných barevných položek | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34e07894c3306f544396e53001990f7b9a2df5a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707792"
---
# <a name="how-to-use-built-in-colorable-items"></a>Postup: Použití vestavěných barevných položek
Před použitím předdefinovaných barevných položek je nutné nejprve signalizovat integrovanému vývojovému prostředí (IDE), že neposkytujete vlastní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> vlastní barevné položky, což by v tomto případě byly objekty. To provést nastavením položky registru pro jazykovou službu.

## <a name="to-use-built-in-colorable-items"></a>Použití vestavěných barevných položek

1. V **části\\ HKEY_LOCAL_MACHINE\VisualStudio<X.Y\\>\Languages\Language Services<Language Name\>**, kde \<X.Y> je verze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a \<název jazyka> je název vašeho jazyka, vytvořte hodnotu položky registru DWORD nazvanou **RequestStockColors**.

2. Nastavte hodnotu položky registru **RequestStockColors** na *hodnotu 1*.

    Po vytvoření položky registru může <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metoda colorizeru použít <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> členy výčtu k vyplnění pole atributů barev pro použití editorem.

   > [!NOTE]
   > Nenastavovat tuto položku registru, pokud poskytujete vlastní barevné položky. Další informace naleznete [v tématu Vlastní barevné položky](../../extensibility/internals/custom-colorable-items.md).

## <a name="see-also"></a>Viz také
- [Syntaxe barvení ve vlastních editorech](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Vybarvení syntaxe ve službě starších jazyků](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementace vybarvení syntaxe](../../extensibility/internals/implementing-syntax-coloring.md)
- [Vlastní barevné položky](../../extensibility/internals/custom-colorable-items.md)
- [Registrace služby staršího jazyka](../../extensibility/internals/registering-a-legacy-language-service2.md)
